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
ms.openlocfilehash: d750087cc000ad31a24d91411c0885a75d59e74f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501941"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Omezení rizik: Dotykové ovládání založená na ukazatelích a podpora pera

Aplikace WPF, které cílí .NET Framework 4.7 a běží v systémech Windows od verze Windows 10 Creators Update můžete povolit volitelné `WM_POINTER`– na základě WPF touch/stylus zásobníku.

## <a name="impact"></a>Dopad

Vývojáři, kteří explicitně nepovolíte podporu dotykového ovládání/stylus založená na ukazatelích měli vidět žádné změny v chování touch/stylus WPF.

Toto jsou aktuální známé problémy s nepovinným `WM_POINTER`– na základě touch/stylus zásobníku:

- Žádná podpora pro rukopis v reálném čase.

   Zatímco rukopis a stylus moduly plug-in i nadále fungovat, jsou spravována na vlákně uživatelského rozhraní, což může vést k nižšímu výkonu.

- Chování změny z důvodu změn v podpoře z dotykového ovládání/stylus událostí na události myši.

  - Manipulace s může chovat jinak.

  - Přetažení nezobrazí odpovídající zpětné vazby pro dotykové ovládání. (Netýká tužkou.)

  - Dotykové ovládání/stylus událostí, nepůjdou už přetažení.

      Aplikace to můžete zablokování potenciálně, dokud je zjištěna vstup z myši. Vývojáři by místo toho zahájit přetáhněte a vyřadit z události myši.

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>Vyjádření výslovného souhlasu s na základě WM_POINTER touch/stylus podpory

Vývojáři, kteří si přejete povolit tento zásobník můžete do souboru app.config své aplikace přidejte následující:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Odebírá se tento záznam a nastaví její hodnotu na `false` vypne této volitelné zásobníku.

## <a name="see-also"></a>Viz také:

- [Změny cílení v rozhraní .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
