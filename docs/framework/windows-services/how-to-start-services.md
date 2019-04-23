---
title: 'Postupy: Spuštění služby'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: db66e8a264bc0381a2ff4689c4427047a158eb32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336834"
---
# <a name="how-to-start-services"></a>Postupy: Spuštění služby
Po dokončení instalace služby musí být spuštěna. Od volání <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodu na třídu služby. Obvykle <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda definuje užitečnou práci, služba bude provádět. Po spuštění služby, zůstane aktivní, dokud je ručně pozastavená nebo zastavená.  
  
 Služby můžete nastavit spustit automaticky nebo ručně. Služba, která se spustí automaticky spustí se při restartování nebo počítače, na kterém je nainstalovaný se nejprve zapnuté. Uživatel musí spustit služba, která se spouští ručně.  
  
> [!NOTE]
>  Ve výchozím nastavení služby vytvořené pomocí sady Visual Studio jsou nastaveny na Manuální spuštění.  
  
 Službu můžete ručně spustit několika způsoby – z **Průzkumníka serveru**, z **správce řízení služeb**, nebo z kódu pomocí komponentu volána <xref:System.ServiceProcess.ServiceController>.  
  
 Můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost <xref:System.ServiceProcess.ServiceInstaller> třídu k určení, zda by měl službu spustit ručně nebo automaticky.  
  
### <a name="to-specify-how-a-service-should-start"></a>Chcete-li určit, jak by měl spustit službu  
  
1. Po vytvoření vaší služby, přidejte nezbytné instalační programy pro něj. Další informace najdete v tématu [jak: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2. V Návrháři klikněte na instalační program služby pro službu, kterou pracujete.  
  
3. V **vlastnosti** okno, nastaveno <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících akcí:  
  
    |Služba instalace|Nastavte tuto hodnotu|  
    |----------------------------------|--------------------|  
    |Po restartování počítače|**Automatické**|  
    |Při spuštění akce explicitní uživatel služby|**Ruční**|  
  
    > [!TIP]
    >  Chcete-li zabránit spuštění vůbec vaši službu, můžete nastavit <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost **zakázané**. To může provést, pokud se chystáte několikrát restartuje server a chcete ušetřit čas tím, že zabráníte služby, které by normálně spustit spuštění.  
  
    > [!NOTE]
    >  Po instalaci služby lze změnit tyto a další vlastnosti.  
  
     Existuje několik způsobů, jak můžete spustit službu, která má jeho <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> procesu nastavena na **ruční** – od **Průzkumníka serveru**, z **správce řízení služeb Windows**, nebo z kódu. Je důležité si uvědomit, že některé z těchto metod ve skutečnosti spustit službu v kontextu **správce řízení služeb**; **Průzkumníka serveru** a programové metody spouštění služby ve skutečnosti manipulaci s řadičem.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Chcete-li službu spustit ručně z Průzkumníka serveru  
  
1. V **Průzkumníka serveru**, přidání serveru, je-li dosud není uložen. Další informace najdete v tématu Postupy: Přístup a inicializace Průzkumníka serveru Průzkumníka databáze.  
  
2. Rozbalte **služby** uzel a pak vyhledejte service, které chcete spustit.  
  
3. Klikněte pravým tlačítkem na název služby a klikněte na tlačítko **Start**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Ruční spuštění služby od správce řízení služeb  
  
1. Otevřít **správce řízení služeb** pomocí jedné z následujících akcí:  
  
    -   V systémech Windows XP a 2000 Professional, klikněte pravým tlačítkem na **tento počítač** na ploše a pak klikněte na tlačítko **spravovat**. V dialogovém okně, které se zobrazí, rozbalte **služeb a aplikací** uzlu.  
  
         \- nebo –  
  
    -   V systému Windows Server 2003 a Windows 2000 Server, klikněte na tlačítko **Start**, přejděte na **programy**, klikněte na tlačítko **nástroje pro správu**a potom klikněte na tlačítko **služby**.  
  
        > [!NOTE]
        >  V systému Windows NT verze 4.0, můžete otevřít toto dialogové z **ovládací panely**.  
  
     Teď byste měli vidět vaše služba uvedená v **služby** části okna.  
  
2. Vyberte svoji službu v seznamu pravým tlačítkem myši a potom klikněte na tlačítko **Start**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Chcete-li službu spustit ručně z kódu  
  
1. Vytvoření instance <xref:System.ServiceProcess.ServiceController> třídy a jeho konfigurace pro interakci se službou, kterou chcete spravovat.  
  
2. Volání <xref:System.ServiceProcess.ServiceController.Start%2A> metoda ke spuštění služby.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Vytvoření služeb Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
