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
# <a name="azure-active-directory"></a><span data-ttu-id="b0743-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b0743-103">Azure Active Directory</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b0743-104">Microsoft Azure Active Directory (Azure AD) nabízí správu identit a přístupu jako službu.</span><span class="sxs-lookup"><span data-stu-id="b0743-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="b0743-105">Zákazníci je používají ke konfiguraci a údržbě uživatelů, k jakým informacím se mají ukládat, kteří mají přístup k těmto informacím, kdo je může spravovat a k jakým aplikacím mají přístup.</span><span class="sxs-lookup"><span data-stu-id="b0743-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="b0743-106">AAD může ověřit uživatele pro aplikace, které jsou nakonfigurované pro použití, a zajistit tak jednotné přihlašování (SSO).</span><span class="sxs-lookup"><span data-stu-id="b0743-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="b0743-107">Dá se používat samostatně nebo integrovat s Windows AD spuštěným místně.</span><span class="sxs-lookup"><span data-stu-id="b0743-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="b0743-108">Služba Azure AD je sestavená pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="b0743-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="b0743-109">Je to skutečně cloudové řešení identity, které používá Graph API a syntaxi OData pro dotazy, na rozdíl od Windows AD, který používá protokol LDAP.</span><span class="sxs-lookup"><span data-stu-id="b0743-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="b0743-110">Místní služba Active Directory může synchronizovat atributy uživatelů s cloudem pomocí služeb synchronizace identit, což umožňuje, aby se veškeré ověřování probíhat v cloudu pomocí Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b0743-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="b0743-111">Alternativně je možné ověřování nakonfigurovat prostřednictvím připojení, aby se vrátilo zpátky do místní služby Active Directory přes AD FS, aby je služba Windows AD dokončila místně.</span><span class="sxs-lookup"><span data-stu-id="b0743-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="b0743-112">Azure AD podporuje obrazovky pro přihlašování pomocí značek společnosti, ověřování více továrn a cloudové proxy aplikace, které slouží k poskytování jednotného přihlašování pro aplikace hostované místně.</span><span class="sxs-lookup"><span data-stu-id="b0743-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="b0743-113">Nabízí různé druhy sestav zabezpečení a možností výstrah.</span><span class="sxs-lookup"><span data-stu-id="b0743-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="b0743-114">Odkazy</span><span class="sxs-lookup"><span data-stu-id="b0743-114">References</span></span>

- [<span data-ttu-id="b0743-115">Platforma Microsoft identity</span><span class="sxs-lookup"><span data-stu-id="b0743-115">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="b0743-116">[Předchozí](authentication-authorization.md)
>[Další](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="b0743-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
