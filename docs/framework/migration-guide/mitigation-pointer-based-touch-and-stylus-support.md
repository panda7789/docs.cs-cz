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
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Zmírnění rizika: dotykové ovládání pomocí ukazatele a Podpora stylusu

Aplikace WPF, které cílí na .NET Framework 4,7 a jsou spuštěné v systémech Windows počínaje systémem Windows 10 Creators Update, mohou povolit volitelnou sadu `WM_POINTER`WPF Touch/Stylus na bázi.

## <a name="impact"></a>Dopad

Vývojáři, kteří explicitně nepovolili podporu dotykového ovládání a stylusu na základě ukazatele, by se v chování WPF Touch/Stylus nezměnily.

Tady jsou uvedené aktuální známé problémy s volitelnou `WM_POINTER`dotykem nebo stylusem na bázi:

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

Odebráním této položky nebo nastavením její hodnoty na `false` dojde k vypnutí tohoto volitelného zásobníku.

## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
