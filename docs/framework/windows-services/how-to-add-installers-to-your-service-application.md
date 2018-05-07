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
manager: douge
ms.openlocfilehash: faece1d7ee752e4c17f39027ff8a97fc95ed451b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-installers-to-your-service-application"></a>Postupy: Přidání instalačních programů do aplikace služby
Visual Studio se dodává instalace součásti, které můžete nainstalovat prostředky přidružené k vaší aplikace služby. Součásti instalace registraci jednotlivých služeb v systému, ke které se instaluje a umožní správci řízení služeb vědět, že služba existuje. Pokud pracujete s aplikací služby, můžete vybrat odkaz v okně vlastností a automaticky tak přidejte příslušné instalační programy do projektu.  
  
> [!NOTE]
>  Hodnoty vlastností pro vaši službu jsou kopírovány z třídu služby k třídě Instalační služby. Pokud aktualizujete hodnoty vlastností v třídě služby, nejsou automaticky aktualizovány v instalačním programu.  
  
 Když přidáte do projektu novou třídu instalační program (který ve výchozím názvem `ProjectInstaller`) je vytvořen v projektu a instancí odpovídající instalace součásti jsou vytvořené v něm. Tato třída slouží jako centrální bod pro všechny součásti instalace je třeba projekt. Například pokud přidat druhý službu do vaší aplikace a klikněte na odkaz přidat instalační program, druhý instalační program třída není vytvořena; Místo toho je nezbytné další instalace součásti pro službu druhý přidat do existující třídy.  
  
 Nemusíte dělat žádné zvláštní kódování v rámci instalační programy, aby vaše služby správně nainstalovány. Však může občas potřebujete upravit obsah instalační programy, pokud je nutné přidat zvláštní funkce do procesu instalace.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-installers-to-your-service-application"></a>K přidání instalačních programů do aplikace služby  
  
1.  V **Průzkumníku řešení**, přístup **návrhu** zobrazení pro danou službu, pro který chcete přidat součást instalace.  
  
2.  Klikněte na pozadí návrháře vybrat službu sám sebe, než všechny její obsah.  
  
3.  Pomocí návrháře fokus, klikněte pravým tlačítkem a pak klikněte na **přidat instalační program**.  
  
     Novou třídu, `ProjectInstaller`a dvě součásti instalace <xref:System.ServiceProcess.ServiceProcessInstaller> a <xref:System.ServiceProcess.ServiceInstaller>, jsou přidány do projektu a hodnoty vlastností pro službu se zkopírují do komponenty.  
  
4.  Klikněte na tlačítko <xref:System.ServiceProcess.ServiceInstaller> součásti a ověřte, že hodnota <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na stejnou hodnotu jako <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost na samotnou službu.  
  
5.  Chcete-li zjistit, jak bude vaše služba spuštěna, klikněte na tlačítko <xref:System.ServiceProcess.ServiceInstaller> součásti a nastavené <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> vlastnost na odpovídající hodnotu.  
  
    |Hodnota|Výsledek|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Služba je třeba spustit ručně, po instalaci. Další informace najdete v tématu [postupy: spuštění služby](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Služba se spustí sám o sobě vždy, když je počítač se restartuje.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Službu nelze spustit.|  
  
6.  Chcete-li určit kontext zabezpečení, ve které vaše služba bude spuštěna, klikněte na tlačítko <xref:System.ServiceProcess.ServiceProcessInstaller> součásti a nastavte hodnoty odpovídající vlastnost. Další informace najdete v tématu [postupy: určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7.  Přepište všechny metody, pro které je třeba provést vlastní zpracování.  
  
8.  Proveďte kroky 1 až 7 pro každý další služby ve vašem projektu.  
  
    > [!NOTE]
    >  U každé další služby ve vašem projektu, je nutné přidat další <xref:System.ServiceProcess.ServiceInstaller> komponentu do projektu `ProjectInstaller` třídy. <xref:System.ServiceProcess.ServiceProcessInstaller> Součást přidali v kroku tři funguje se všemi instalační programy jednotlivé služby v projektu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Postupy: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Postupy: Určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
