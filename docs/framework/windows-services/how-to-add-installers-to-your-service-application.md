---
title: 'Postupy: Přidání instalačních programů do aplikace služby'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
ms.openlocfilehash: 99e2376c50f0b47cc21002b2926818707188805e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053654"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Postupy: Přidání instalačních programů do aplikace služby
Visual Studio dodává součásti pro instalaci, které mohou instalovat prostředky přidružené k vašim aplikacím služby. Instalační součásti registrují jednotlivé služby v systému, do kterého se instaluje, a umožněte správci řízení služeb zjistit, že služba existuje. Při práci s aplikací služby můžete vybrat odkaz v okno Vlastnosti k automatickému přidání příslušných instalačních programů do projektu.  
  
> [!NOTE]
> Hodnoty vlastností vaší služby se zkopírují z třídy služby do instalační třídy. Pokud aktualizujete hodnoty vlastností u třídy služby, nebudou automaticky aktualizovány v instalačním programu.  
  
 Přidáte-li do projektu instalační program, je v projektu vytvořena nová třída (ve výchozím nastavení je pojmenována `ProjectInstaller`) a v rámci ní jsou vytvořeny instance příslušných instalačních komponent. Tato třída slouží jako centrální bod pro všechny součásti instalace, které váš projekt potřebuje. Pokud například přidáte do aplikace druhou službu a kliknete na odkaz Přidat instalační program, není vytvořena druhá třída instalačního programu. místo toho je do existující třídy přidána nutná dodatečná instalační součást pro druhou službu.  
  
 V rámci instalačních programů není nutné provádět žádné speciální kódování, aby se vaše služby nainstalovaly správně. Někdy však může být nutné změnit obsah instalačních programů, pokud potřebujete do procesu instalace přidat speciální funkce.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>Přidání instalačních programů do aplikace služby  
  
1. V **Průzkumník řešení**zobrazení **návrhu** přístupu ke službě, pro kterou chcete přidat instalační komponentu.  
  
2. Kliknutím na pozadí návrháře vyberte samotnou službu, nikoli její obsah.  
  
3. V návrháři se zaostřením klikněte pravým tlačítkem myši a pak klikněte na **Přidat instalační program**.  
  
     Nové třídy `ProjectInstaller`, a dvě instalační komponenty <xref:System.ServiceProcess.ServiceProcessInstaller> a <xref:System.ServiceProcess.ServiceInstaller>, jsou přidány do projektu a hodnoty vlastností služby jsou zkopírovány do komponent.  
  
4. Klikněte na <xref:System.ServiceProcess.ServiceInstaller> součást a ověřte, zda je hodnota <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnosti nastavena na stejnou hodnotu jako <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost v samotné službě.  
  
5. Chcete-li zjistit, jak bude služba spuštěna, klikněte <xref:System.ServiceProcess.ServiceInstaller> na součást a nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na příslušnou hodnotu.  
  
    |Hodnota|Výsledek|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Služba musí být po instalaci spuštěna ručně. Další informace naleznete v tématu [How to: Start Services](how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Služba se spustí při každém restartování počítače.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Službu nelze spustit.|  
  
6. Chcete-li určit kontext zabezpečení, ve kterém bude služba spuštěna, klikněte <xref:System.ServiceProcess.ServiceProcessInstaller> na součást a nastavte příslušné hodnoty vlastností. Další informace naleznete v tématu [How to: Určete kontext zabezpečení pro služby](how-to-specify-the-security-context-for-services.md).  
  
7. Přepište všechny metody, pro které potřebujete provést vlastní zpracování.  
  
8. Proveďte kroky 1 až 7 pro každou další službu v projektu.  
  
    > [!NOTE]
    > Pro každou další službu v projektu je nutné přidat další <xref:System.ServiceProcess.ServiceInstaller> komponentu do `ProjectInstaller` třídy projektu. <xref:System.ServiceProcess.ServiceProcessInstaller> Součást přidaná v kroku tři funguje se všemi jednotlivými instalátory služby v projektu.  
  
## <a name="see-also"></a>Viz také

- [Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: Instalace a odinstalace služeb](how-to-install-and-uninstall-services.md)
- [Postupy: Spuštění služeb](how-to-start-services.md)
- [Postupy: Určení kontextu zabezpečení pro služby](how-to-specify-the-security-context-for-services.md)
