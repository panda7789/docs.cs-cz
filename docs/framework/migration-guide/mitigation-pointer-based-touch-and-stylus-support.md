---
title: 'Omezení rizik: Dotykové ovládání založená na ukazatelích a podpora pera'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9264d8eb7923663061f9bccfffe5b8f5254549f0
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379892"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="2a30c-102">Omezení rizik: Dotykové ovládání založená na ukazatelích a podpora pera</span><span class="sxs-lookup"><span data-stu-id="2a30c-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="2a30c-103">Aplikace WPF, které cílí .NET Framework 4.7 a běží v systémech Windows od verze Windows 10 Creators Update můžete povolit volitelné `WM_POINTER`– na základě WPF touch/stylus zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2a30c-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="2a30c-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="2a30c-104">Impact</span></span>

<span data-ttu-id="2a30c-105">Vývojáři, kteří explicitně nepovolíte podporu dotykového ovládání/stylus založená na ukazatelích měli vidět žádné změny v chování touch/stylus WPF.</span><span class="sxs-lookup"><span data-stu-id="2a30c-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="2a30c-106">Toto jsou aktuální známé problémy s nepovinným `WM_POINTER`– na základě touch/stylus zásobníku:</span><span class="sxs-lookup"><span data-stu-id="2a30c-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="2a30c-107">Žádná podpora pro rukopis v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="2a30c-107">No support for real-time inking.</span></span>

   <span data-ttu-id="2a30c-108">Zatímco rukopis a stylus moduly plug-in i nadále fungovat, jsou spravována na vlákně uživatelského rozhraní, což může vést k nižšímu výkonu.</span><span class="sxs-lookup"><span data-stu-id="2a30c-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="2a30c-109">Chování změny z důvodu změn v podpoře z dotykového ovládání/stylus událostí na události myši.</span><span class="sxs-lookup"><span data-stu-id="2a30c-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="2a30c-110">Manipulace s může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="2a30c-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="2a30c-111">Přetažení nezobrazí odpovídající zpětné vazby pro dotykové ovládání.</span><span class="sxs-lookup"><span data-stu-id="2a30c-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="2a30c-112">(Netýká tužkou.)</span><span class="sxs-lookup"><span data-stu-id="2a30c-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="2a30c-113">Dotykové ovládání/stylus událostí, nepůjdou už přetažení.</span><span class="sxs-lookup"><span data-stu-id="2a30c-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="2a30c-114">To může potenciálně způsobit aplikace přestane reagovat, dokud se detekuje vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="2a30c-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="2a30c-115">Vývojáři by místo toho zahájit přetáhněte a vyřadit z události myši.</span><span class="sxs-lookup"><span data-stu-id="2a30c-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="2a30c-116">Vyjádření výslovného souhlasu s na základě WM_POINTER touch/stylus podpory</span><span class="sxs-lookup"><span data-stu-id="2a30c-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="2a30c-117">Vývojáři, kteří si přejete povolit tento zásobník můžete do souboru app.config své aplikace přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="2a30c-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="2a30c-118">Odebírá se tento záznam a nastaví její hodnotu na `false` vypne této volitelné zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2a30c-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a30c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a30c-119">See also</span></span>

- [<span data-ttu-id="2a30c-120">Změny cílení v rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2a30c-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
