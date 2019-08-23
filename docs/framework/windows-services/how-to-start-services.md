---
title: 'Postupy: Spuštění služby'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 3544f7d846ecf68ed5ed01812b9c69b295c63c69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952416"
---
# <a name="how-to-start-services"></a>Postupy: Spuštění služby
Po instalaci služby je nutné ji spustit. Spouští se <xref:System.ServiceProcess.ServiceBase.OnStart%2A> volání metody třídy služby. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Metoda obvykle definuje užitečnou práci, kterou bude služba provádět. Po spuštění služby zůstane aktivní, dokud není ručně pozastavená nebo zastavená.  
  
 Služby je možné nastavit tak, aby se spouštěly automaticky nebo ručně. Služba, která se spustí automaticky, se spustí při restartování počítače, ve kterém je nainstalovaný, nebo nejdřív zapnutý. Uživatel musí spustit službu, která se spustí ručně.  
  
> [!NOTE]
> Ve výchozím nastavení se služby vytvořené pomocí sady Visual Studio nastaví tak, aby se spouštěly ručně.  
  
 Existuje několik způsobů, jak ručně spustit službu – od **Průzkumník serveru**, od **správce řízení služeb**nebo z kódu pomocí <xref:System.ServiceProcess.ServiceController>komponenty s názvem.  
  
 Nastavením <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnosti<xref:System.ServiceProcess.ServiceInstaller> třídy určíte, zda má být služba spuštěna ručně nebo automaticky.  
  
### <a name="to-specify-how-a-service-should-start"></a>Určení způsobu spuštění služby  
  
1. Po vytvoření služby přidejte pro ni potřebné instalační programy. Další informace najdete v tématu [jak: Přidejte instalační programy do aplikace](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)služby.  
  
2. V návrháři klikněte na instalační program služby pro službu, se kterou pracujete.  
  
3. V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na jednu z následujících možností:  
  
    |Instalace služby|Nastavit tuto hodnotu|  
    |----------------------------------|--------------------|  
    |Po restartování počítače|**Automatické**|  
    |Když akce explicitního uživatele spustí službu|**Zásah**|  
  
    > [!TIP]
    >  Pokud chcete zabránit tomu, aby se služba spustila vůbec, můžete <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost nastavit na **zakázáno**. To můžete provést, pokud budete Server několikrát restartovat a chcete ušetřit čas tím, že znemožníte službám, které by normálně začaly začít.  
  
    > [!NOTE]
    > Tyto a další vlastnosti se dají po instalaci služby změnit.  
  
     Existuje několik způsobů, jak můžete spustit službu, která má svůj <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> proces nastavený na **Ruční** – od **Průzkumník serveru**, od **správce řízení služeb systému Windows**nebo z kódu. Je důležité si uvědomit, že ne všechny tyto metody ve skutečnosti zahájí službu v kontextu **správce řízení služeb**; **Průzkumník serveru** a programové metody spuštění služby skutečně manipulují s řadičem.  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a>Ruční spuštění služby z Průzkumník serveru  
  
1. V **Průzkumník serveru**přidejte server, který chcete, pokud již není uveden. Další informace naleznete v tématu How to: Přístup a inicializace Průzkumník serveru – Průzkumník databáze  
  
2. Rozbalte uzel **služby** a vyhledejte službu, kterou chcete spustit.  
  
3. Klikněte pravým tlačítkem na název služby a pak klikněte na **Spustit**.  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a>Ruční spuštění služby ze Správce řízení služeb  
  
1. Pomocí jedné z následujících akcí otevřete **správce řízení služeb** :  
  
    - V systému Windows XP a 2000 Professional klikněte pravým tlačítkem na položku **Tento počítač** na ploše a pak klikněte na možnost **Spravovat**. V dialogovém okně, které se zobrazí, rozbalte uzel **služby a aplikace** .  
  
         \- nebo –  
  
    - V systému Windows Server 2003 a Windows 2000 Server klikněte na **Start**, přejděte na **programy**, klikněte na **Nástroje pro správu**a potom klikněte na **služby**.  
  
        > [!NOTE]
        >  V systému Windows NT verze 4,0 můžete toto dialogové okno otevřít z **ovládacích panelů**.  
  
     Teď by se měla zobrazit vaše služba uvedená v části **služby** v okně.  
  
2. V seznamu vyberte svou službu, klikněte na ni pravým tlačítkem myši a pak klikněte na **Spustit**.  
  
### <a name="to-manually-start-a-service-from-code"></a>Ruční spuštění služby z kódu  
  
1. Vytvořte instanci <xref:System.ServiceProcess.ServiceController> třídy a nakonfigurujte ji pro interakci se službou, kterou chcete spravovat.  
  
2. <xref:System.ServiceProcess.ServiceController.Start%2A> Zavolejte metodu pro spuštění služby.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Vytvořit služby systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
