---
title: 'Postupy: Zápis uživatelských nastavení při běhu pomocí C#'
description: Naučte se, jak psát nastavení v době běhu v jazyce C# tím, že se změny nastavení mezi relacemi aplikací zachovají zavoláním metody Save.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904322"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Postupy: zápis uživatelských nastavení v době běhu pomocí jazyka C\#

Nastavení, která jsou v oboru aplikace, jsou jen pro čtení a lze je změnit pouze v době návrhu nebo změnou souboru. config v mezi relacemi aplikace. Nastavení, která jsou v uživatelském rozsahu, však lze zapsat v době běhu stejně, jako byste změnili jakoukoli hodnotu vlastnosti. Nová hodnota zůstává po dobu trvání relace aplikace. Změny nastavení mezi relacemi aplikace můžete zachovat voláním metody Save.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Postupy: zápis a zachování uživatelských nastavení za běhu pomocí jazyka C\#
  
1. Nastavte přístup k nastavení a přiřaďte mu novou hodnotu, jak je znázorněno v následujícím příkladu:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Chcete-li zachovat změny nastavení mezi relacemi aplikace, zavolejte metodu Save, jak je znázorněno v tomto příkladu:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Uživatelská nastavení se ukládají do souboru v podsložce složky místní skrytá data aplikace daného uživatele.  
  
## <a name="see-also"></a>Viz také

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Postupy: Čtení uživatelských nastavení při běhu pomocí C#](how-to-read-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
