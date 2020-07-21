---
title: 'Zmírnění: vlastní implementace IMessageFilter. PreFilterMessage'
description: Přečtěte si o vlastních IMessageFilter. PreFilterMessage implementaci obsažených v aplikacích model Windows Forms, které cílí na .NET Framework 4.6.1 a novějších.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475252"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="dbaaf-103">Zmírnění: vlastní implementace IMessageFilter. PreFilterMessage</span><span class="sxs-lookup"><span data-stu-id="dbaaf-103">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="dbaaf-104">V model Windows Forms aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> může vlastní implementace bezpečně filtrovat zprávy při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody, pokud <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:</span><span class="sxs-lookup"><span data-stu-id="dbaaf-104">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="dbaaf-105">Provede jednu nebo obě následující akce:</span><span class="sxs-lookup"><span data-stu-id="dbaaf-105">Does one or both of the following:</span></span>

  - <span data-ttu-id="dbaaf-106">Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dbaaf-106">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="dbaaf-107">Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dbaaf-107">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="dbaaf-108">Metoda.</span><span class="sxs-lookup"><span data-stu-id="dbaaf-108">method.</span></span>

- <span data-ttu-id="dbaaf-109">**A** zprávy pumpy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dbaaf-109">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="dbaaf-110">Dopad</span><span class="sxs-lookup"><span data-stu-id="dbaaf-110">Impact</span></span>

<span data-ttu-id="dbaaf-111">Tato změna má vliv pouze na aplikace model Windows Forms, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="dbaaf-111">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="dbaaf-112">Pro model Windows Forms aplikace cílené na předchozí verze .NET Framework taková implementace v některých případech vyvolá <xref:System.IndexOutOfRangeException> výjimku při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání metody.</span><span class="sxs-lookup"><span data-stu-id="dbaaf-112">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="dbaaf-113">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="dbaaf-113">Mitigation</span></span>

<span data-ttu-id="dbaaf-114">Pokud je tato změna nežádoucí, můžou se aplikace, které cílí na .NET Framework 4.6.1 nebo novější verze, odhlásit, a to přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="dbaaf-114">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="dbaaf-115">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 nebo novější verzi, se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="dbaaf-115">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="dbaaf-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbaaf-116">See also</span></span>

- [<span data-ttu-id="dbaaf-117">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="dbaaf-117">Application compatibility</span></span>](application-compatibility.md)
