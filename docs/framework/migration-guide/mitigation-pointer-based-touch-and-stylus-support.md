---
title: 'Zmírnění: Podpora dotykového ovládání a stylusu založené na ukazateli'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094472"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="881b9-102">Zmírnění: Podpora dotykového ovládání a stylusu založené na ukazateli</span><span class="sxs-lookup"><span data-stu-id="881b9-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="881b9-103">WPF aplikace, které cílí na rozhraní .NET Framework 4.7 a běží v `WM_POINTER`systému Windows počínaje aktualizací Windows 10 Creators Update, mohou povolit volitelný zásobník dotykového a stylusu WPF založené na vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="881b9-103">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="881b9-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="881b9-104">Impact</span></span>

<span data-ttu-id="881b9-105">Vývojáři, kteří explicitně nepovolují podporu dotykového ovládání nebo pera založené na ukazateli, by neměli vidět žádnou změnu v chování dotykového a stylusu WPF.</span><span class="sxs-lookup"><span data-stu-id="881b9-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="881b9-106">Následují aktuální známé problémy `WM_POINTER`s volitelným zásobníkem dotykového ovládání a pera:</span><span class="sxs-lookup"><span data-stu-id="881b9-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="881b9-107">Žádná podpora pro rukopis v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="881b9-107">No support for real-time inking.</span></span>

   <span data-ttu-id="881b9-108">Zatímco rukopis a stylus pluginy stále fungují, jsou zpracovány ve vlákně uživatelského rozhraní, což může vést ke špatnému výkonu.</span><span class="sxs-lookup"><span data-stu-id="881b9-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="881b9-109">Změny chování v důsledku změn v propagaci z touch/stylus událostí na události myši.</span><span class="sxs-lookup"><span data-stu-id="881b9-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="881b9-110">Manipulace se může chovat jinak.</span><span class="sxs-lookup"><span data-stu-id="881b9-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="881b9-111">Přetažením nezobrazí odpovídající zpětnou vazbu pro dotykové ovládání.</span><span class="sxs-lookup"><span data-stu-id="881b9-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="881b9-112">(To nemá vliv na vstup pera.)</span><span class="sxs-lookup"><span data-stu-id="881b9-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="881b9-113">Drag/Drop již nelze spustit při událostech dotykového/stylusu.</span><span class="sxs-lookup"><span data-stu-id="881b9-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="881b9-114">To může potenciálně způsobit, že aplikace přestane reagovat, dokud není zjištěn vstup myši.</span><span class="sxs-lookup"><span data-stu-id="881b9-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="881b9-115">Místo toho by vývojáři měli zahájit přetahování z událostí myši.</span><span class="sxs-lookup"><span data-stu-id="881b9-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="881b9-116">Přihlášení k podpoře dotykového ovládání a stylusu na bázi WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="881b9-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="881b9-117">Vývojáři, kteří chtějí povolit tento zásobník, mohou do souboru *app.config* své aplikace přidat následující.</span><span class="sxs-lookup"><span data-stu-id="881b9-117">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="881b9-118">Odebrání této položky nebo `false` nastavení její hodnoty vypne tento volitelný zásobník.</span><span class="sxs-lookup"><span data-stu-id="881b9-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="881b9-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="881b9-119">See also</span></span>

- [<span data-ttu-id="881b9-120">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="881b9-120">Application compatibility</span></span>](application-compatibility.md)
