---
title: "Omezení rizik: Na základě ukazatel Touch a podporu pera"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
caps.latest.revision: "2"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78a7365d9bc82111ebd27f40e999c24d8f9ebfde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="e4929-102">Omezení rizik: Na základě ukazatel Touch a podporu pera</span><span class="sxs-lookup"><span data-stu-id="e4929-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="e4929-103">WPF aplikace, které cílí rozhraní .NET Framework 4.7 a běží na systémy Windows od verze Windows 10 Creators Update můžete povolit volitelné `WM_POINTER`– na základě WPF touch/pera zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e4929-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="e4929-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="e4929-104">Impact</span></span>

<span data-ttu-id="e4929-105">Vývojáři, kteří explicitně nepovolujte podpory na základě ukazatel touch/pera měli vidět žádná změna v chování touch/pera WPF.</span><span class="sxs-lookup"><span data-stu-id="e4929-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="e4929-106">Toto jsou aktuální známé problémy s nepovinným `WM_POINTER`– na základě touch/pera zásobníku:</span><span class="sxs-lookup"><span data-stu-id="e4929-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="e4929-107">Žádné podporou kreslení v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="e4929-107">No support for real-time inking.</span></span>

   <span data-ttu-id="e4929-108">Při rukopisu a pera modulů plug-in i nadále fungovat, jsou zpracovávány ve vlákně UI, což může vést k nižšímu výkonu.</span><span class="sxs-lookup"><span data-stu-id="e4929-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="e4929-109">Chování změny z důvodu změn v povýšení z událostí touch/pera na události myši.</span><span class="sxs-lookup"><span data-stu-id="e4929-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="e4929-110">Manipulace s může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="e4929-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="e4929-111">Přetažením nezobrazí odpovídající zpětnou vazbu pro dotykové ovládání.</span><span class="sxs-lookup"><span data-stu-id="e4929-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="e4929-112">(To nemá vliv pera vstup.)</span><span class="sxs-lookup"><span data-stu-id="e4929-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="e4929-113">Přetažením lze inicializovat už na událostí touch/pera.</span><span class="sxs-lookup"><span data-stu-id="e4929-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="e4929-114">To potenciálně může na aplikace, dokud je zjištěna vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="e4929-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="e4929-115">Místo toho by vývojáři Zahájit přetažení a vyřadit z událostí myši.</span><span class="sxs-lookup"><span data-stu-id="e4929-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="e4929-116">Vyjádření výslovného souhlasu s podporu na základě WM_POINTER touch/pera</span><span class="sxs-lookup"><span data-stu-id="e4929-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="e4929-117">Vývojáři, kteří chtějí povolit tento zásobník můžete přidat následující do souboru app.config jejich aplikace:</span><span class="sxs-lookup"><span data-stu-id="e4929-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="e4929-118">Odebrání této položky nebo nastavení její hodnoty na `false` vypne této volitelné zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e4929-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4929-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4929-119">See also</span></span>

[<span data-ttu-id="e4929-120">Změny cílení v rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="e4929-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
