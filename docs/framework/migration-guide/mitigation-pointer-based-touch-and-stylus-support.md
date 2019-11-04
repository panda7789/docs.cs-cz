---
title: 'Zmírnění rizika: dotykové ovládání pomocí ukazatele a Podpora stylusu'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 6b3e8068be2f5ed82c483b760fe100ea0a751588
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457858"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="ca66e-102">Zmírnění rizika: dotykové ovládání pomocí ukazatele a Podpora stylusu</span><span class="sxs-lookup"><span data-stu-id="ca66e-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="ca66e-103">Aplikace WPF, které cílí na .NET Framework 4,7 a jsou spuštěné v systémech Windows počínaje systémem Windows 10 Creators Update, mohou povolit volitelnou sadu `WM_POINTER`WPF Touch/Stylus na bázi.</span><span class="sxs-lookup"><span data-stu-id="ca66e-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="ca66e-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="ca66e-104">Impact</span></span>

<span data-ttu-id="ca66e-105">Vývojáři, kteří explicitně nepovolili podporu dotykového ovládání a stylusu na základě ukazatele, by se v chování WPF Touch/Stylus nezměnily.</span><span class="sxs-lookup"><span data-stu-id="ca66e-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="ca66e-106">Tady jsou uvedené aktuální známé problémy s volitelnou `WM_POINTER`dotykem nebo stylusem na bázi:</span><span class="sxs-lookup"><span data-stu-id="ca66e-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="ca66e-107">Žádná podpora pro psaní rukou v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="ca66e-107">No support for real-time inking.</span></span>

   <span data-ttu-id="ca66e-108">I když rukopisné moduly plug-in a stylusy jsou stále funkční, jsou zpracovávány ve vlákně uživatelského rozhraní, což může vést k špatnému výkonu.</span><span class="sxs-lookup"><span data-stu-id="ca66e-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="ca66e-109">Změny chování z důvodu změn v povýšení událostí dotykové/Stylus na události myši.</span><span class="sxs-lookup"><span data-stu-id="ca66e-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="ca66e-110">Manipulace se může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="ca66e-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="ca66e-111">Přetažením nebudete mít k dispozici odpovídající zpětnou vazbu k dotykovému vstupu.</span><span class="sxs-lookup"><span data-stu-id="ca66e-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="ca66e-112">(To nemá vliv na vstup stylusu.)</span><span class="sxs-lookup"><span data-stu-id="ca66e-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="ca66e-113">Přetažení už nejde iniciovat na událostech Touch/stylusu.</span><span class="sxs-lookup"><span data-stu-id="ca66e-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="ca66e-114">To může potenciálně způsobit, že aplikace přestane reagovat, dokud se nezjistí vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="ca66e-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="ca66e-115">Místo toho by vývojáři měli zahájit přetahování z událostí myši.</span><span class="sxs-lookup"><span data-stu-id="ca66e-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="ca66e-116">PřiWM_POINTERte se k podpoře dotykového ovládání a stylusu.</span><span class="sxs-lookup"><span data-stu-id="ca66e-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="ca66e-117">Vývojáři, kteří chtějí tuto sadu povolit, mohou do souboru App. config aplikace přidat následující:</span><span class="sxs-lookup"><span data-stu-id="ca66e-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="ca66e-118">Odebráním této položky nebo nastavením její hodnoty na `false` dojde k vypnutí tohoto volitelného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ca66e-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca66e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca66e-119">See also</span></span>

- [<span data-ttu-id="ca66e-120">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="ca66e-120">Application compatibility</span></span>](application-compatibility.md)
