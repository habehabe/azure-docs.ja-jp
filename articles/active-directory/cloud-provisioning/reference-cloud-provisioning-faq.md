---
title: Azure AD Connect クラウド プロビジョニングに関する FAQ
description: このドキュメントでは、クラウド プロビジョニングに関してよく寄せられる質問について説明します。
services: active-directory
author: billmath
manager: daveba
ms.service: active-directory
ms.workload: identity
ms.topic: overview
ms.date: 02/26/2020
ms.subservice: hybrid
ms.author: billmath
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbc1baa86bb81c8975587e84427a72ccc044805e
ms.sourcegitcommit: c2065e6f0ee0919d36554116432241760de43ec8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "77916576"
---
# <a name="azure-active-directory-connect-faq"></a>Azure Active Directory Connect に関する FAQ

Azure Active Directory (Azure AD) Connect クラウド プロビジョニングに関してよく寄せられる質問をお読みください。

## <a name="general-installation"></a>一般的なインストール

**Q:クラウド プロビジョニングが実行される頻度は?**

クラウド プロビジョニングは、2 分おきに実行されるようスケジュールされています。 2 分おきに、ユーザー、グループ、パスワード ハッシュの変更がすべて、Azure AD にプロビジョニングされます。

**Q:パスワード ハッシュ同期が初回実行時にエラーになります。なぜですか?**

これは予期されることです。 このエラーは、ユーザー オブジェクトが Azure AD に存在しないことが原因で発生します。 ユーザーが Azure AD にプロビジョニングされると、パスワード ハッシュはその後の実行でプロビジョニングされます。 何度か実行されるのを待ってから、パスワード ハッシュ同期のエラーが発生しないことを確認してください。

**Q:Active Directory インスタンスに、クラウドのプロビジョニングでサポートされていない属性 (ディレクトリ拡張機能など) がある場合はどうなりますか。**

クラウド プロビジョニングが実行され、サポートされている属性がプロビジョニングされます。 サポートされていない属性は、Azure AD にプロビジョニングされません。 Active Directory でディレクトリ拡張機能を確認し、これらの属性を Azure AD に持ち込む必要がないことを確認してください。 必要な属性がある場合は、Azure AD Connect 同期を使用するか、必要な情報をサポートされている属性の 1 つ (たとえば、拡張属性 1 から 15) に移動することを検討してください。

**Q:Azure AD Connect 同期とクラウド プロビジョニングの違いは何ですか?**

Azure AD Connect 同期では、プロビジョニングがオンプレミスの同期サーバーで実行されます。 構成は、オンプレミスの同期サーバーに格納されます。 Azure AD Connect のクラウド プロビジョニングでは、プロビジョニングの構成はクラウドに格納され、Azure AD プロビジョニング サービスの一環としてクラウドで実行されます。 

**Q:クラウド プロビジョニングを使用して複数の Active Directory フォレストから同期することはできますか?**

はい。 クラウド プロビジョニングを使用すると、複数の Active Directory フォレストから同期することができます。 複数フォレスト環境では、すべての参照 (マネージャーなど) がドメイン内に存在する必要があります。  

**Q:エージェントはどのように更新されますか?**

エージェントは、Microsoft によって自動的にアップグレードされます。 その結果、エージェントの新しいバージョンのテストや検証に伴う IT 部門の負担が軽減されます。 

**Q:自動アップグレードを無効にすることはできますか?**

自動アップグレードを無効にするためのサポートされた方法はありません。

**Q:クラウド プロビジョニングのソース アンカーは変更できますか?**

クラウド プロビジョニングでは、既定で、ソース アンカーとして ObjectGUID へのフォールバックが設定された ms-ds-consistency-GUID が使用されます。 ソース アンカーを変更するためのサポートされた方法はありません。

**Q:クラウド プロビジョニングを使用すると、新しいサービス プリンシパルが AD ドメイン名と一緒に表示されます。これは予想どおりですか?**

はい。クラウド プロビジョニングでは、プロビジョニング構成用のサービス プリンシパルが作成されますが、そのサービス プリンシパル名としてドメイン名が使用されます。 サービス プリンシパルの構成は変更しないでください。

**Q:同期済みユーザーが次回ログオン時にパスワードの変更を要求される場合はどうなりますか?**

クラウド プロビジョニングでパスワード ハッシュ同期が有効になっていて、同期済みユーザーがオンプレミス AD への次回ログオン時にパスワードの変更を要求される場合、変更予定のパスワード ハッシュは Azure AD にプロビジョニングされません。 ユーザーがパスワードを変更すると、ユーザー パスワード ハッシュが AD から Azure AD にプロビジョニングされます。

**Q:クラウド プロビジョニングでは、オブジェクトの ms-ds-consistencyGUID の書き戻しがサポートされていますか?**

いいえ。いずれのオブジェクト (ユーザー オブジェクトを含む) についても ms-ds-consistencyGUID の書き戻しはサポートされません。 

**Q:クラウド プロビジョニングを使用してユーザーをプロビジョニングしています。構成を削除しました。Azure AD に古い同期済みオブジェクトが表示されたままなのはなぜですか?** 

構成を削除しても、Azure AD 内の同期済みオブジェクトがクラウド プロビジョニングによってクリーンアップされることはありません。 古いオブジェクトが表示されないようにするには、構成のスコープを空のグループまたは組織単位に変更します。 プロビジョニングが実行されてオブジェクトがクリーンアップされたら、構成を無効にして削除してください。 

**Q:Exchange ハイブリッドがサポートされないことには、どのような意味があるのですか?**

Exchange ハイブリッド展開機能を利用すると、オンプレミスと Office 365 で Exchange メールボックスが共存できるようになります。 Azure AD Connect により、Azure AD の特定の属性セットがオンプレミスのディレクトリに同期されます。  現在クラウド プロビジョニング エージェントでは、これらの属性がオンプレミス ディレクトリに同期されません。したがって、クラウド プロビジョニング エージェントは、Azure AD Connect を置き換える機能としてはサポートされません。

**Q:クラウド プロビジョニング エージェントを Windows Server Core にインストールすることはできますか?**

いいえ。Server Core へのエージェントのインストールはサポートされません。

## <a name="next-steps"></a>次のステップ 

- [プロビジョニングとは](what-is-provisioning.md)
- [Azure AD Connect クラウド プロビジョニングとは](what-is-cloud-provisioning.md)
