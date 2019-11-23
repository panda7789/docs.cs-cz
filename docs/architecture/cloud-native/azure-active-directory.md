---
title: Azure Active Directory
description: Architekt cloudových nativních aplikací .NET pro Azure | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 207043507a9052c47683383a98cef6417a1a2740
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183691"
---
# <a name="azure-active-directory"></a>Azure Active Directory

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Microsoft Azure Active Directory (Azure AD) nabízí správu identit a přístupu jako službu. Zákazníci je používají ke konfiguraci a údržbě uživatelů, k jakým informacím se mají ukládat, kteří mají přístup k těmto informacím, kdo je může spravovat a k jakým aplikacím mají přístup. AAD může ověřit uživatele pro aplikace, které jsou nakonfigurované pro použití, a zajistit tak jednotné přihlašování (SSO). Dá se používat samostatně nebo integrovat s Windows AD spuštěným místně.

Služba Azure AD je sestavená pro Cloud. Je to skutečně cloudové řešení identity, které používá Graph API a syntaxi OData pro dotazy, na rozdíl od Windows AD, který používá protokol LDAP. Místní služba Active Directory může synchronizovat atributy uživatelů s cloudem pomocí služeb synchronizace identit, což umožňuje, aby se veškeré ověřování probíhat v cloudu pomocí Azure AD. Alternativně je možné ověřování nakonfigurovat prostřednictvím připojení, aby se vrátilo zpátky do místní služby Active Directory přes AD FS, aby je služba Windows AD dokončila místně.

Azure AD podporuje obrazovky pro přihlašování pomocí značek společnosti, ověřování více továrn a cloudové proxy aplikace, které slouží k poskytování jednotného přihlašování pro aplikace hostované místně. Nabízí různé druhy sestav zabezpečení a možností výstrah.

## <a name="references"></a>Reference

- [Platforma Microsoft identity](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
>[Předchozí](authentication-authorization.md)
>[Další](identity-server.md)
