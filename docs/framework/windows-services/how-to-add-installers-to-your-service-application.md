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
ms.openlocfilehash: af56e01c1c8c1e23bb80413ce6f52a5f6d467b4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914118"
---
# <a name="how-to-add-installers-to-your-service-application"></a>Postupy: Přidání instalačních programů do aplikace služby
Visual Studio se dodáván instalace součásti, které můžete nainstalovat prostředky spojené s aplikací služeb. Součásti instalace registraci jednotlivých služeb v systému, na který se instaluje a umožní správci řízení služeb vědět, jestli existuje služba. Při práci s aplikací služby, můžete vybrat odkaz v okně Vlastnosti na příslušné instalační programy automaticky přidat do projektu.  
  
> [!NOTE]
>  Hodnoty vlastností pro vaši službu jsou kopírovány z třídu služby na třídu Instalační služby. Při aktualizaci hodnot vlastností na třídu služby, nejsou automaticky aktualizovány v instalačním programu.  
  
 Když přidáte do projektu novou třídu instalační program (který, ve výchozím nastavení, se nazývá `ProjectInstaller`) vytvořen v projektu a instance příslušné instalační součásti jsou vytvořeny v rámci něj. Tato třída slouží jako centrální bod pro všechny součásti instalace je třeba projekt. Například Pokud Přidání druhé služby pro vaši aplikaci a klikněte na odkaz přidat instalační program, druhá třída instalační program není vytvořena; Místo toho potřebné další instalační komponenty pro druhou službu se přidá do existující třídy.  
  
 Nemusíte dělat žádné zvláštní psaní kódu v rámci instalačních programů do vaší služby správně nainstalovat. Však může čas od času potřeba upravit obsah instalační programy, pokud je potřeba přidat zvláštní funkce do procesu instalace.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-installers-to-your-service-application"></a>K přidání instalačních programů do aplikace služby  
  
1. V **Průzkumníka řešení**, přístup **návrhu** zobrazení pro službu, pro který chcete přidat jako součást instalace.  
  
2. Klikněte na pozadí návrháře vyberte službu, sama, nikoli některé z jejích komponent.  
  
3. Má Návrhář fokus, klikněte pravým tlačítkem a pak klikněte na tlačítko **přidat instalační program**.  
  
     Nová třída `ProjectInstaller`a dvě součásti instalace <xref:System.ServiceProcess.ServiceProcessInstaller> a <xref:System.ServiceProcess.ServiceInstaller>, se přidají do vašeho projektu a hodnoty vlastností pro službu se zkopírují do komponenty.  
  
4. Klikněte na tlačítko <xref:System.ServiceProcess.ServiceInstaller> komponenty a ověřte, zda hodnota <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> je nastavena na stejnou hodnotu jako <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> vlastnost na samotnou službu.  
  
5. Pokud chcete zjistit, jak bude vaše služba spuštěna, klikněte na tlačítko <xref:System.ServiceProcess.ServiceInstaller> komponenty a nastavte <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> k odpovídající hodnotě.  
  
    |Hodnota|Výsledek|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|Tuto službu musí ručně spustit po instalaci. Další informace najdete v tématu [jak: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md).|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|Služba se spustí sám o sobě pokaždé, když se počítač se restartuje.|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|Službu nelze spustit.|  
  
6. K určení kontextu zabezpečení, ve kterém se spustí vaše služba, klikněte na tlačítko <xref:System.ServiceProcess.ServiceProcessInstaller> komponenty a nastavte vlastnost odpovídající hodnoty. Další informace najdete v tématu [jak: Určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).  
  
7. Přepište všechny metody, pro které je potřeba provést vlastní zpracování.  
  
8. Proveďte kroky 1 až 7 pro každý další služby ve vašem projektu.  
  
    > [!NOTE]
    >  U každé další služby ve vašem projektu, je nutné přidat další <xref:System.ServiceProcess.ServiceInstaller> komponentu do projektu `ProjectInstaller` třídy. <xref:System.ServiceProcess.ServiceProcessInstaller> Komponenty přidali v kroku 3 funguje se všemi instalační programy jednotlivé služby v projektu.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Postupy: Instalace a odinstalace služeb](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Postupy: Spuštění služeb](../../../docs/framework/windows-services/how-to-start-services.md)
- [Postupy: Určení kontextu zabezpečení pro služby](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
