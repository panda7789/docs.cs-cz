---
title: Přehled aplikačního modelu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 258e3862da79e78510991df26cc286c7231ad097
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464096"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Přehled aplikačního modelu jazyka Visual Basic
Visual Basic poskytuje pro řízení chování aplikací modelu Windows Forms dobře definovaný model: model aplikace Visual Basic. Tento model obsahuje události pro zpracování aplikace při spuštění a vypnutí, jakož i události pro zachycení neošetřené výjimky. Také poskytuje podporu pro vývoj aplikací s jednou instancí. Aplikační model je rozšiřitelný, takže vývojáři, kteří potřebují mít větší kontrolu můžete přizpůsobit jeho přepisovatelné metody.  
  
## <a name="uses-for-the-application-model"></a>Používá pro aplikační Model  
 Typická aplikace potřebuje k provádění úloh po spuštění a vypnutí. Například při spuštění, aplikace může zobrazit úvodní obrazovku, zkontrolujte připojení k databázi, načíst do uloženého stavu atd. Při vypnutí aplikace ji ukončete připojení k databázi, uložit aktuální stav a tak dále. Kromě toho může aplikace spustit konkrétní kód při vypnutí aplikace neočekávaném ukončení, například jako během neošetřenou výjimku.  
  
 Model aplikace Visual Basic umožňuje snadno vytvořit *jednou instancí* aplikace. Aplikace s jedinou instancí se liší od běžné aplikace, který pouze jedna instance aplikace může běžet současně. Pokus o spuštění jiná instance aplikace s jedinou instancí výsledků v původní instanci oznamované – prostřednictvím `StartupNextInstance` události –, který byl proveden další pokus o spuštění. Oznámení obsahuje další instance argumenty příkazového řádku. Další instance aplikace pak zavřen před všechny inicializace může dojít.  
  
 Aplikace s jedinou instancí se spustí a zkontroluje, zda je první instance nebo další instance aplikace:  
  
-   Pokud je první instance, spustí běžným způsobem.  
  
-   Každý další pokus o spuštění aplikace, zatímco první instance je spuštěná, má za následek velmi odlišné chování. Následné pokusy o upozorní na první instanci o argumenty příkazového řádku a okamžitě se ukončí. První instance zpracuje `StartupNextInstance` události a určit, co argumenty příkazového řádku další instance byly a nadále běží.  
  
     Tento diagram znázorňuje, jak další instance signály první instance:  
  
     ![Diagram zobrazující průběh bitové kopie jedné instance aplikace.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 Pomocí manipulace `StartupNextInstance` událostí, můžete řídit chování vaší aplikace s jedinou instancí. Například aplikace Microsoft Outlook obvykle běží jako jedinou instancí aplikace; Když při spuštěném Outlooku a při pokusu o spuštění aplikace Outlook znovu, se pozornost zaměří na původní instanci, ale jiná instance neotevře.  
  
## <a name="events-in-the-application-model"></a>Události v aplikační Model  
 Tyto události jsou součástí aplikačního modelu:  
  
-   **Spuštění aplikace**. Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událost při spuštění. Díky zpracování této události, můžete přidat kód, který aplikaci inicializuje před načtením hlavního formuláře. `Startup` Událost také poskytuje pro zrušení spuštění aplikace v průběhu této fáze procesu spuštění v případě potřeby.  
  
     Můžete nakonfigurovat aplikaci chcete zobrazit úvodní obrazovku při spuštění kódu po spuštění aplikace. Ve výchozím nastavení, aplikační model potlačí úvodní obrazovku v případě buď `/nosplash` nebo `-nosplash` se používá argument příkazového řádku.  
  
-   **Aplikace s jednou instancí**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Událost se vyvolá, když se spustí další instance aplikace s jedinou instancí. Události předá argumenty příkazového řádku další instance.  
  
-   **Neošetřené výjimky**. Pokud dojde k neošetřené výjimce v aplikaci, vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událostí. Vaše obslužná rutina pro tuto událost můžete zkoumat výjimky a určit, jestli se má pokračovat v provádění.  
  
     `UnhandledException` v některých případech není vyvolána událost. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Připojení k síti změny**. Pokud se změní dostupnosti sítě v počítači aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> událostí.  
  
     `NetworkAvailabilityChanged` v některých případech není vyvolána událost. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Vypnout aplikaci**. Aplikace poskytuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> události signalizuje, že pokud má vypršet jeho vypnutí. V tomto případě obslužná rutina, abyste měli jistotu, že operace vaše aplikace potřebuje k provedení – zavření a uložení, například – jsou dokončeny. Můžete nakonfigurovat aplikaci pro vypnutí při zavření hlavního formuláře nebo vypnout pouze, když zavřete všechny formuláře.  
  
## <a name="availability"></a>Dostupnost  
 Ve výchozím nastavení model aplikace Visual Basic je k dispozici pro projekty Windows Forms. Pokud konfigurace aplikace pro použití jiné spouštěcí objekt, nebo začněte kódu aplikace s vlastní `Sub Main`, pak tento objekt nebo třída může být nutné zadat implementaci <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy k použití modelu aplikací. Informace o změně spouštěcí objekt najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
