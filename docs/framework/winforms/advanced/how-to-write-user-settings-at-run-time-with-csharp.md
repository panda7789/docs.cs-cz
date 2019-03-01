---
title: 'Postupy: Zápis uživatelských nastavení při běhu pomocíC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981592"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Postupy: Zápis uživatelských nastavení při běhu pomocí C\#

Nastavení oboru aplikace jsou jen pro čtení a lze změnit pouze v době návrhu nebo úpravou souboru .config mezi jednotlivými relacemi aplikace. Nastavení, která jsou s rozsahem uživatele, ale může být napsán v době běhu stejně jako jakoukoli hodnotu vlastnosti. Nová hodnota se uchovávají po dobu trvání relace aplikace. Je možné zachovat změny nastavení mezi relacemi aplikace po zavolání metody uložit.  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Postupy: Zápis a zachování uživatelského nastavení při běhu pomocí C\#
  
1. Přístup k nastavení a přiřaďte ji novou hodnotu, jak je znázorněno v tomto příkladu:  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. Pokud chcete, a zachová tak změny v nastavení mezi relacemi aplikace, zavolejte metodu uložit, jak je znázorněno v tomto příkladu:  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
Uživatelská nastavení jsou uloženy do souboru do podsložky složky místní skryté aplikace data uživatele.  
  
## <a name="see-also"></a>Viz také:

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Postupy: Čtení uživatelských nastavení při běhu pomocíC#](how-to-read-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
