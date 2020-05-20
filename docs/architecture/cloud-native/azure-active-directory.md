---
title: Azure Active Directory
description: Architekt cloudových nativních aplikací .NET pro Azure | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 03f5ea8e84bc3c4a2a88a63d4b109aabf0c64f36
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614276"
---
# <a name="azure-active-directory"></a>Azure Active Directory

Microsoft Azure Active Directory (Azure AD) nabízí správu identit a přístupu jako službu. Zákazníci je používají ke konfiguraci a údržbě uživatelů, k jakým informacím se mají ukládat, kteří mají přístup k těmto informacím, kdo je může spravovat a k jakým aplikacím mají přístup. AAD může ověřit uživatele pro aplikace, které jsou nakonfigurované pro použití, a zajistit tak jednotné přihlašování (SSO). Dá se používat samostatně nebo integrovat s Windows AD spuštěným místně.

Služba Azure AD je sestavená pro Cloud. Je to skutečně cloudové řešení identity, které používá Graph API a syntaxi OData pro dotazy, na rozdíl od Windows AD, který používá protokol LDAP. Místní služba Active Directory může synchronizovat atributy uživatelů s cloudem pomocí služeb synchronizace identit, což umožňuje, aby se veškeré ověřování probíhat v cloudu pomocí Azure AD. Alternativně je možné ověřování nakonfigurovat prostřednictvím připojení, aby se vrátilo zpátky do místní služby Active Directory přes AD FS, aby je služba Windows AD dokončila místně.

Azure AD podporuje obrazovky pro přihlašování pomocí značek společnosti, ověřování více továrn a cloudové proxy aplikace, které slouží k poskytování jednotného přihlašování pro aplikace hostované místně. Nabízí různé druhy sestav zabezpečení a možností výstrah.

## <a name="references"></a>Odkazy

- [Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Předchozí](authentication-authorization.md) 
> [Další](identity-server.md)
