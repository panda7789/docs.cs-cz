---
title: Zmírnění Dotyková podpora na základě ukazatele a stylusu
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67e41450ed69d73a4b27b0aa37974ae01be69687
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779237"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Zmírnění Dotyková podpora na základě ukazatele a stylusu

Aplikace WPF, které cílí na .NET Framework 4,7 a jsou spuštěné v systémech Windows počínaje systémem Windows 10 Creators Update, mohou `WM_POINTER`povolit volitelnou sadu WPF Touch/stylusu.

## <a name="impact"></a>Dopad

Vývojáři, kteří explicitně nepovolili podporu dotykového ovládání a stylusu na základě ukazatele, by se v chování WPF Touch/Stylus nezměnily.

Tady jsou uvedené aktuální známé problémy s volitelným `WM_POINTER`tónovým nebo stylusem stackem:

- Žádná podpora pro psaní rukou v reálném čase.

   I když rukopisné moduly plug-in a stylusy jsou stále funkční, jsou zpracovávány ve vlákně uživatelského rozhraní, což může vést k špatnému výkonu.

- Změny chování z důvodu změn v povýšení událostí dotykové/Stylus na události myši.

  - Manipulace se může chovat jinak.

  - Přetažením nebudete mít k dispozici odpovídající zpětnou vazbu k dotykovému vstupu. (To nemá vliv na vstup stylusu.)

  - Přetažení už nejde iniciovat na událostech Touch/stylusu.

      To může potenciálně způsobit, že aplikace přestane reagovat, dokud se nezjistí vstup z myši. Místo toho by vývojáři měli zahájit přetahování z událostí myši.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>PřiWM_POINTERte se k podpoře dotykového ovládání a stylusu.

Vývojáři, kteří chtějí tuto sadu povolit, mohou do souboru App. config aplikace přidat následující:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Odebráním této položky nebo nastavením její hodnoty `false` dojde k vypnutí tohoto volitelného zásobníku.

## <a name="see-also"></a>Viz také:

- [Změna cílení změn v .NET Framework 4,7](retargeting-changes-in-the-net-framework-4-7.md)
