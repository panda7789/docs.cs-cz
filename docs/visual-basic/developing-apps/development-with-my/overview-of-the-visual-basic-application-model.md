---
title: Přehled aplikačního modelu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 5194810574f594e2c117fef8d8998b7ecebbc981
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-the-visual-basic-application-model"></a>Přehled aplikačního modelu jazyka Visual Basic
Visual Basic poskytuje dobře definovaný model pro řízení chování aplikací modelu Windows Forms: model aplikace Visual Basic. Tento model zahrnuje události pro zpracování aplikace spuštění a vypnutí, a také události pro zachycení neošetřených výjimek. Také poskytuje podporu pro vývoj aplikací jedné instance. Aplikační model je rozšiřitelný, takže vývojáři, kteří potřebují větší kontrolu můžete přizpůsobit jeho přepisovatelné metody.  
  
## <a name="uses-for-the-application-model"></a>Používá pro Model aplikace  
 Typická aplikace potřebuje k provádění úloh, při spuštění a vypnutí. Například při spuštění, aplikace můžete zobrazí úvodní obrazovka, vytvořit připojení k databázi, načíst do uloženého stavu a tak dále. Při vypnutí aplikace, můžete zavřít připojení databáze, uložit aktuální stav a tak dále. Kromě toho může aplikace provést určitý kód při ukončení aplikace neočekávaném ukončení, například jako během k neošetřené výjimce.  
  
 Model aplikace Visual Basic umožňuje snadné vytváření *jedné instance* aplikace. Aplikace s jedinou instancí liší od běžné aplikace v tom, že může být pouze jedna instance aplikace spuštěná v čase. Pokus o spuštění jiná instance aplikace s jedinou instancí výsledkem původní instanci – prostřednictvím `StartupNextInstance` událostí – které byla vytvořena další pokus o spuštění. Oznámení obsahuje další instance argumenty příkazového řádku. Další instance aplikace je pak uzavřen, než dojde k všechny inicializace.  
  
 Aplikace s jedinou instancí spustí a zkontroluje, zda je první instance nebo další instanci aplikace:  
  
-   Pokud je první instance, spustí běžným způsobem.  
  
-   Každý další pokus o spuštění aplikace, v průběhu první instance, výsledkem velmi různé chování. Následující pokus upozorní první instance o argumenty příkazového řádku a okamžitě se ukončí. První instance zpracuje `StartupNextInstance` událostí určit, jaké další instance argumenty příkazového řádku byly a nadále spuštěna.  
  
     Tento diagram znázorňuje, jak další instance signály první instance.  
  
     ![Jedna Instance aplikace Image](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 Ve zpracování `StartupNextInstance` událostí, můžete řídit chování vaší aplikace s jedinou instancí. Například Microsoft Outlook obvykle běží jako jednoduchou aplikaci; Při spuštění aplikace Outlook a při pokusu o spuštění aplikace Outlook znovu přesouvá fokus na původní instanci, ale jiná instance se neotevře.  
  
## <a name="events-in-the-application-model"></a>Události v modelu aplikace  
 V modelu aplikace byly nalezeny následující události:  
  
-   **Spuštění aplikace**. Aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí po jeho spuštění. Při zpracování této událost, můžete přidat kód, který inicializuje aplikace před načtením hlavní formulář. `Startup` Událostí také poskytuje pro zrušení spuštění aplikace v průběhu této fáze procesu spuštění v případě potřeby.  
  
     Můžete nakonfigurovat aplikace zobrazí úvodní obrazovka při spouštění kódu aplikace. Ve výchozím nastavení, potlačí model aplikace úvodní obrazovku v případě buď `/nosplash` nebo `-nosplash` argument příkazového řádku se používá.  
  
-   **Jednou instancí aplikace**. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> Událost se vyvolá, když se spustí další instanci aplikace s jedinou instancí. Událost předá argumenty příkazového řádku následné instance.  
  
-   **Neošetřené výjimky**. Pokud aplikace dojde k neošetřené výjimce, vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> událostí. Vaší obslužné rutiny pro tuto událost můžete prozkoumat výjimku a určit, jestli pokračovat v provádění.  
  
     `UnhandledException` Událost se vyvolá, v některých případech. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
-   **Připojení k síti změny**. Pokud se změní dostupnost sítě pro počítače, aplikace vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> událostí.  
  
     `NetworkAvailabilityChanged` Událost se vyvolá, v některých případech. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
-   **Vypnout aplikaci**. Aplikace poskytuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událost, která má být signalizován je vypnout. V tomto případě obslužnou rutinu, můžete zkontrolovat, že operace, které aplikace potřebuje k provedení – zavření a uložení, například – dokončení. Můžete nakonfigurovat aplikaci vypnout hlavní formulář zavře, nebo je vypnout pouze, když zavřete všechny formuláře.  
  
## <a name="availability"></a>Dostupnost  
 Ve výchozím nastavení je k dispozici pro projekty Windows Forms model aplikace Visual Basic. Pokud konfigurace aplikace pro použití různých spouštěcích objektu, nebo začněte kódu aplikace s vlastní `Sub Main`, pak tento objekt nebo třída třeba poskytnout implementaci <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy pomocí modelu aplikace. Informace o změně spouštěcí objekt najdete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
