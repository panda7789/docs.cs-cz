---
title: Zmírnění Vlastní implementace IMessageFilter. PreFilterMessage
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af81468c5c4c4caf2f09725d6c7c4723084e35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779429"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="d9d4f-102">Zmírnění Vlastní implementace IMessageFilter. PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="d9d4f-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="d9d4f-103">V model Windows Forms aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, může vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace bezpečně filtrovat zprávy <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> při volání <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> metody, pokud implementace:</span><span class="sxs-lookup"><span data-stu-id="d9d4f-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="d9d4f-104">Provede jednu nebo obě následující akce:</span><span class="sxs-lookup"><span data-stu-id="d9d4f-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="d9d4f-105">Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="d9d4f-106">Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="d9d4f-107">Metoda.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-107">method.</span></span>

- <span data-ttu-id="d9d4f-108">**A** zprávy pumpy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="d9d4f-109">Dopad</span><span class="sxs-lookup"><span data-stu-id="d9d4f-109">Impact</span></span>

<span data-ttu-id="d9d4f-110">Tato změna má vliv pouze na aplikace model Windows Forms, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="d9d4f-111">Pro model Windows Forms aplikace cílené na předchozí verze .NET Framework taková implementace v některých případech vyvolá <xref:System.IndexOutOfRangeException> výjimku <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> při volání metody.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="d9d4f-112">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="d9d4f-112">Mitigation</span></span>

<span data-ttu-id="d9d4f-113">Pokud je tato změna nežádoucí, můžou se aplikace, které cílí na .NET Framework 4.6.1 nebo novější verze, odhlásit, a to přidáním následujícího nastavení konfigurace do [ \<části > modulu runtime](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="d9d4f-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="d9d4f-114">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale jsou spuštěné v .NET Framework 4.6.1 nebo novější verzi, se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [ \<části běhového prostředí >](../configure-apps/file-schema/runtime/runtime-element.md) konfigurační soubor aplikace:</span><span class="sxs-lookup"><span data-stu-id="d9d4f-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="d9d4f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9d4f-115">See also</span></span>

- [<span data-ttu-id="d9d4f-116">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="d9d4f-116">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
