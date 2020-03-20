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
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Zmírnění: Podpora dotykového ovládání a stylusu založené na ukazateli

WPF aplikace, které cílí na rozhraní .NET Framework 4.7 a běží v `WM_POINTER`systému Windows počínaje aktualizací Windows 10 Creators Update, mohou povolit volitelný zásobník dotykového a stylusu WPF založené na vlastnostech.

## <a name="impact"></a>Dopad

Vývojáři, kteří explicitně nepovolují podporu dotykového ovládání nebo pera založené na ukazateli, by neměli vidět žádnou změnu v chování dotykového a stylusu WPF.

Následují aktuální známé problémy `WM_POINTER`s volitelným zásobníkem dotykového ovládání a pera:

- Žádná podpora pro rukopis v reálném čase.

   Zatímco rukopis a stylus pluginy stále fungují, jsou zpracovány ve vlákně uživatelského rozhraní, což může vést ke špatnému výkonu.

- Změny chování v důsledku změn v propagaci z touch/stylus událostí na události myši.

  - Manipulace se může chovat jinak.

  - Přetažením nezobrazí odpovídající zpětnou vazbu pro dotykové ovládání. (To nemá vliv na vstup pera.)

  - Drag/Drop již nelze spustit při událostech dotykového/stylusu.

      To může potenciálně způsobit, že aplikace přestane reagovat, dokud není zjištěn vstup myši. Místo toho by vývojáři měli zahájit přetahování z událostí myši.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Přihlášení k podpoře dotykového ovládání a stylusu na bázi WM_POINTER

Vývojáři, kteří chtějí povolit tento zásobník, mohou do souboru *app.config* své aplikace přidat následující.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Odebrání této položky nebo `false` nastavení její hodnoty vypne tento volitelný zásobník.

## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
