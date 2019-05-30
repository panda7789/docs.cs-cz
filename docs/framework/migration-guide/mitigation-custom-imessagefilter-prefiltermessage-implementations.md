---
title: 'Omezení rizik: Custom IMessageFilter.PreFilterMessage Implementations'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3ac43b574c4382c4aec5070acde0fa77516727d
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251138"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="b47e4-102">Omezení rizik: Custom IMessageFilter.PreFilterMessage Implementations</span><span class="sxs-lookup"><span data-stu-id="b47e4-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="b47e4-103">V aplikacích Windows Forms, s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.6.1, vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace může bezpečně filtru zprávy, když <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána, pokud <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:</span><span class="sxs-lookup"><span data-stu-id="b47e4-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="b47e4-104">Provede jednu nebo obě z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b47e4-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="b47e4-105">Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b47e4-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="b47e4-106">Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b47e4-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="b47e4-107">Metoda.</span><span class="sxs-lookup"><span data-stu-id="b47e4-107">method.</span></span>

- <span data-ttu-id="b47e4-108">**A** čerpadla zprávy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b47e4-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="b47e4-109">Dopad</span><span class="sxs-lookup"><span data-stu-id="b47e4-109">Impact</span></span>

<span data-ttu-id="b47e4-110">Tato změna ovlivní pouze aplikace Windows Forms, s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="b47e4-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="b47e4-111">Pro aplikace Windows Forms, které cílí na předchozí verze rozhraní .NET Framework, vyvolá tato implementace v některých případech <xref:System.IndexOutOfRangeException> výjimka při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody</span><span class="sxs-lookup"><span data-stu-id="b47e4-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="b47e4-112">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="b47e4-112">Mitigation</span></span>

<span data-ttu-id="b47e4-113">Pokud tuto změnu nežádoucí, aplikace, které cílí .NET Framework 4.6.1 nebo novější verze můžete zrušit ho tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="b47e4-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="b47e4-114">Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6.1 nebo novější můžete přejít k toto chování tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="b47e4-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="b47e4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b47e4-115">See also</span></span>

- [<span data-ttu-id="b47e4-116">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="b47e4-116">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
