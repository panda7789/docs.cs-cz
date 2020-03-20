---
title: 'Zmírnění: Vlastní implementace iMessageFilter.PreFilterMessageMessageMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400118"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="a1c32-102">Zmírnění: Vlastní implementace iMessageFilter.PreFilterMessageMessageMessage</span><span class="sxs-lookup"><span data-stu-id="a1c32-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="a1c32-103">V aplikacích pro Windows Forms, které cílí na verze rozhraní .NET Framework <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> počínaje rozhraním .NET Framework 4.6.1, může vlastní implementace bezpečně filtrovat zprávy při volání <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metody, pokud je <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:</span><span class="sxs-lookup"><span data-stu-id="a1c32-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="a1c32-104">Má jeden nebo oba z následujících:</span><span class="sxs-lookup"><span data-stu-id="a1c32-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="a1c32-105">Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a1c32-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="a1c32-106">Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a1c32-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="a1c32-107">Metoda.</span><span class="sxs-lookup"><span data-stu-id="a1c32-107">method.</span></span>

- <span data-ttu-id="a1c32-108">**A** pumpuje zprávy <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="a1c32-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="a1c32-109">Dopad</span><span class="sxs-lookup"><span data-stu-id="a1c32-109">Impact</span></span>

<span data-ttu-id="a1c32-110">Tato změna ovlivní pouze aplikace pro Windows Forms, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="a1c32-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="a1c32-111">Pro aplikace pro Windows Forms, které cílí na předchozí verze rozhraní <xref:System.IndexOutOfRangeException> .NET <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> Framework, tyto implementace v některých případech vyvolat výjimku při volání metody</span><span class="sxs-lookup"><span data-stu-id="a1c32-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="a1c32-112">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="a1c32-112">Mitigation</span></span>

<span data-ttu-id="a1c32-113">Pokud je tato změna nežádoucí, aplikace, které cílí na rozhraní .NET Framework 4.6.1 nebo [ \<](../configure-apps/file-schema/runtime/runtime-element.md) novější verzi, se z ní mohou odhlásit přidáním následujícího nastavení konfigurace do části runtime>konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="a1c32-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="a1c32-114">Kromě toho se aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rámci rozhraní .NET Framework [ \<](../configure-apps/file-schema/runtime/runtime-element.md) 4.6.1 nebo novější verze, mohou přihlásit k tomuto chování přidáním následujícího nastavení konfigurace do části konfigurace konfiguračního souboru aplikace>běhu:</span><span class="sxs-lookup"><span data-stu-id="a1c32-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="a1c32-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1c32-115">See also</span></span>

- [<span data-ttu-id="a1c32-116">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="a1c32-116">Application compatibility</span></span>](application-compatibility.md)
