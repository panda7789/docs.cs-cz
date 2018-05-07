---
title: 'Postupy: Spuštění služeb'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
manager: douge
ms.openlocfilehash: 3c8382d2e425d11dc8aa8b22e361b3cc5637744f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-start-services"></a>Postupy: Spuštění služeb
Po instalaci služby musí být spuštěna. Počáteční počet volání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu v třídě služby. Obvykle <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definuje užitečné pracovní službu provede. Po spuštění služby, zůstane aktivní, dokud je ručně pozastavená nebo zastavená.  
  
 Služby můžete nastavit spustit automaticky nebo ručně. Služba, která spouští se automaticky spustila, když je počítač, ve kterém je nainstalován restartoval nebo nejprve zapnutý. Uživatel musí spustit službu, která spustí ručně.  
  
> [!NOTE]
>  Ve výchozím nastavení jsou nastavené služby vytvořené pomocí sady Visual Studio spustit ručně.  
  
 Existuje několik způsobů, můžete ručně spustit službu – z **Průzkumníka serveru**, z **správci řízení služeb**, nebo pomocí součásti volat z kódu <xref:System.ServiceProcess.ServiceController>.  
  
 Můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceInstaller> třídu k určení, zda by měl službu spustit ručně nebo automaticky.  
  
### <a name="to-specify-how-a-service-should-start"></a>K určení toho, jak služba by se měl spustit  
  
1.  Po vytvoření služby, přidejte potřebné instalační programy pro ni. Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  V Návrháři klikněte na instalační program služby pro službu, kterou pracujete.  
  
3.  V **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících akcí:  
  
    |Služba instalace|Nastavení této hodnoty|  
    |----------------------------------|--------------------|  
    |Při restartování počítače|**Automatické**|  
    |Když akce explicitní uživatel spustí službu|**Ruční**|  
  
    > [!TIP]
    >  Chcete-li zabránit spuštění vůbec služby, můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost **zakázané**. To třeba udělat, pokud se chystáte restartovat server několikrát a chcete ušetřit čas tím, že služby, které by normálně spustit spuštění.  
  
    > [!NOTE]
    >  Tyto a další vlastnosti můžete změnit po instalaci služby.  
  
     Existuje několik způsobů, můžete spustit službu, která má jeho <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> proces nastaven na **ruční** – z **Průzkumníka serveru**, z **správci řízení služeb systému Windows**, nebo z kódu. Je důležité si uvědomit, ne všechny tyto metody ve skutečnosti spusťte službu v kontextu **správci řízení služeb**; **Průzkumníka serveru** a programové metody spouštění služby ve skutečnosti manipulaci kontroleru.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Chcete-li službu spustit ručně z Průzkumníka serveru  
  
1.  V **Průzkumníka serveru**, přidejte server, je-li již není uveden. Další informace najdete v tématu Postupy: přístup a inicializaci Průzkumníka databáze Průzkumníka serveru.  
  
2.  Rozbalte **služby** uzel a vyhledejte službu, kterou chcete spustit.  
  
3.  Klikněte pravým tlačítkem na název služby a klikněte na tlačítko **spustit**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Ručně spustit službu ze Správce řízení služeb  
  
1.  Otevřete **správci řízení služeb** jedním z následujících akcí:  
  
    -   V systému Windows XP a 2000 Professional, klikněte pravým tlačítkem na **Můj počítač** na ploše a pak klikněte na tlačítko **spravovat**. V dialogovém okně, které se zobrazí, rozbalte **služeb a aplikací** uzlu.  
  
         \- nebo –  
  
    -   V systému Windows Server 2003 a Windows 2000 Server, klikněte na **spustit**, přejděte na příkaz **programy**, klikněte na tlačítko **nástroje pro správu**a pak klikněte na tlačítko **služby**.  
  
        > [!NOTE]
        >  V systému Windows NT verze 4.0, můžete otevřít dialogové okno z **ovládací panely**.  
  
     Teď byste měli vidět služby uvedené v **služby** části okna.  
  
2.  V seznamu vyberte služby, klikněte pravým tlačítkem ji a pak klikněte na tlačítko **spustit**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Chcete-li službu spustit ručně z kódu  
  
1.  Vytvoření instance <xref:System.ServiceProcess.ServiceController> třídy a nakonfigurovat ji pro interakci s službou, které chcete spravovat.  
  
2.  Volání <xref:System.ServiceProcess.ServiceController.Start%2A> metoda spuštění služby.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
