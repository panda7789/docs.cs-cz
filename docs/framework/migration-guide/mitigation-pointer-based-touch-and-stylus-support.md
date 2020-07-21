---
title: 'Zmírnění rizika: dotykové ovládání pomocí ukazatele a Podpora stylusu'
description: Přečtěte si o účincích povolení volitelného zásobníku WPF Touch/Stylus pro aplikace WPF, které cílí na .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475421"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="b7910-103">Zmírnění rizika: dotykové ovládání pomocí ukazatele a Podpora stylusu</span><span class="sxs-lookup"><span data-stu-id="b7910-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="b7910-104">Aplikace WPF, které cílí na .NET Framework 4,7 a jsou spuštěné ve Windows počínaje verzí Windows 10 Creators Update, můžou povolit volitelnou `WM_POINTER` sadu WPF Touch/stylusu.</span><span class="sxs-lookup"><span data-stu-id="b7910-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="b7910-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="b7910-105">Impact</span></span>

<span data-ttu-id="b7910-106">Vývojáři, kteří explicitně nepovolili podporu dotykového ovládání a stylusu na základě ukazatele, by se v chování WPF Touch/Stylus nezměnily.</span><span class="sxs-lookup"><span data-stu-id="b7910-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="b7910-107">Tady jsou uvedené aktuální známé problémy s volitelným `WM_POINTER` tónovým nebo stylusem stackem:</span><span class="sxs-lookup"><span data-stu-id="b7910-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="b7910-108">Žádná podpora pro psaní rukou v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="b7910-108">No support for real-time inking.</span></span>

   <span data-ttu-id="b7910-109">I když rukopisné moduly plug-in a stylusy jsou stále funkční, jsou zpracovávány ve vlákně uživatelského rozhraní, což může vést k špatnému výkonu.</span><span class="sxs-lookup"><span data-stu-id="b7910-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="b7910-110">Změny chování z důvodu změn v povýšení událostí dotykové/Stylus na události myši.</span><span class="sxs-lookup"><span data-stu-id="b7910-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="b7910-111">Manipulace se může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="b7910-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="b7910-112">Přetažením nebudete mít k dispozici odpovídající zpětnou vazbu k dotykovému vstupu.</span><span class="sxs-lookup"><span data-stu-id="b7910-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="b7910-113">(To nemá vliv na vstup stylusu.)</span><span class="sxs-lookup"><span data-stu-id="b7910-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="b7910-114">Přetažení už nejde iniciovat na událostech Touch/stylusu.</span><span class="sxs-lookup"><span data-stu-id="b7910-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="b7910-115">To může potenciálně způsobit, že aplikace přestane reagovat, dokud se nezjistí vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="b7910-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="b7910-116">Místo toho by vývojáři měli zahájit přetahování z událostí myši.</span><span class="sxs-lookup"><span data-stu-id="b7910-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="b7910-117">Když se přihlásíte k WM_POINTER dotyková Podpora stylusu nebo tužky</span><span class="sxs-lookup"><span data-stu-id="b7910-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="b7910-118">Vývojáři, kteří chtějí tuto sadu povolit, mohou do souboru *app.config* aplikace přidat následující:</span><span class="sxs-lookup"><span data-stu-id="b7910-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="b7910-119">Odebráním této položky nebo nastavením její hodnoty `false` dojde k vypnutí tohoto volitelného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b7910-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7910-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7910-120">See also</span></span>

- [<span data-ttu-id="b7910-121">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="b7910-121">Application compatibility</span></span>](application-compatibility.md)
