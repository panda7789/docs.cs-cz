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
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Zmírnění rizika: dotykové ovládání pomocí ukazatele a Podpora stylusu

Aplikace WPF, které cílí na .NET Framework 4,7 a jsou spuštěné ve Windows počínaje verzí Windows 10 Creators Update, můžou povolit volitelnou `WM_POINTER` sadu WPF Touch/stylusu.

## <a name="impact"></a>Dopad

Vývojáři, kteří explicitně nepovolili podporu dotykového ovládání a stylusu na základě ukazatele, by se v chování WPF Touch/Stylus nezměnily.

Tady jsou uvedené aktuální známé problémy s volitelným `WM_POINTER` tónovým nebo stylusem stackem:

- Žádná podpora pro psaní rukou v reálném čase.

   I když rukopisné moduly plug-in a stylusy jsou stále funkční, jsou zpracovávány ve vlákně uživatelského rozhraní, což může vést k špatnému výkonu.

- Změny chování z důvodu změn v povýšení událostí dotykové/Stylus na události myši.

  - Manipulace se může chovat jinak.

  - Přetažením nebudete mít k dispozici odpovídající zpětnou vazbu k dotykovému vstupu. (To nemá vliv na vstup stylusu.)

  - Přetažení už nejde iniciovat na událostech Touch/stylusu.

      To může potenciálně způsobit, že aplikace přestane reagovat, dokud se nezjistí vstup z myši. Místo toho by vývojáři měli zahájit přetahování z událostí myši.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Když se přihlásíte k WM_POINTER dotyková Podpora stylusu nebo tužky

Vývojáři, kteří chtějí tuto sadu povolit, mohou do souboru *app.config* aplikace přidat následující:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Odebráním této položky nebo nastavením její hodnoty `false` dojde k vypnutí tohoto volitelného zásobníku.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
