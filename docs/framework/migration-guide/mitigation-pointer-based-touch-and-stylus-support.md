---
title: 'Omezení rizik: Na základě ukazatel Touch a podporu pera'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da7d55b34bc21f0c11f13565d017587b4276bad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387777"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Omezení rizik: Na základě ukazatel Touch a podporu pera

WPF aplikace, které cílí rozhraní .NET Framework 4.7 a běží na systémy Windows od verze Windows 10 Creators Update můžete povolit volitelné `WM_POINTER`– na základě WPF touch/pera zásobníku.

## <a name="impact"></a>Dopad

Vývojáři, kteří explicitně nepovolujte podpory na základě ukazatel touch/pera měli vidět žádná změna v chování touch/pera WPF.

Toto jsou aktuální známé problémy s nepovinným `WM_POINTER`– na základě touch/pera zásobníku:

- Žádné podporou kreslení v reálném čase.

   Při rukopisu a pera modulů plug-in i nadále fungovat, jsou zpracovávány ve vlákně UI, což může vést k nižšímu výkonu.

- Chování změny z důvodu změn v povýšení z událostí touch/pera na události myši.

  - Manipulace s může chovat jinak.

  - Přetažením nezobrazí odpovídající zpětnou vazbu pro dotykové ovládání. (To nemá vliv pera vstup.)

  - Přetažením lze inicializovat už na událostí touch/pera.

      To potenciálně může na aplikace, dokud je zjištěna vstup z myši. Místo toho by vývojáři Zahájit přetažení a vyřadit z událostí myši.

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>Vyjádření výslovného souhlasu s podporu na základě WM_POINTER touch/pera

Vývojáři, kteří chtějí povolit tento zásobník můžete přidat následující do souboru app.config jejich aplikace:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Odebrání této položky nebo nastavení její hodnoty na `false` vypne této volitelné zásobníku.

## <a name="see-also"></a>Viz také

[Změny cílení v rozhraní .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
