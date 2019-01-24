---
title: 'Postupy: Zápis uživatelských nastavení při běhu pomocíC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: a62bf540ebdc383f26bd4aed760b2562437047aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560934"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>Postupy: Zápis uživatelských nastavení při běhu pomocíC# #
Nastavení oboru aplikace jsou jen pro čtení a lze změnit pouze v době návrhu nebo úpravou souboru .config mezi jednotlivými relacemi aplikace. Nastavení, která jsou s rozsahem uživatele, ale může být napsán v době běhu stejně jako jakoukoli hodnotu vlastnosti. Nová hodnota se uchovávají po dobu trvání relace aplikace. Je možné zachovat změny nastavení mezi relacemi aplikace po zavolání metody uložit.  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>Postupy: Zápis a zachování uživatelského nastavení při běhu pomocíC#  
  
1.  Přístup k nastavení a přiřaďte ji novou hodnotu, jak je znázorněno v tomto příkladu:  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  Pokud chcete, a zachová tak změny v nastavení mezi relacemi aplikace, zavolejte metodu uložit, jak je znázorněno v tomto příkladu:  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     Uživatelská nastavení jsou uloženy do souboru do podsložky složky místní skryté aplikace data uživatele.  
  
## <a name="see-also"></a>Viz také:
- [Použití nastavení aplikace a uživatelských nastavení](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Postupy: Čtení uživatelských nastavení při běhu pomocíC#](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
