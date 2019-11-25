---
title: Přehled aplikačního modelu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: aa47304cf2bded93bdb95ffe7dfa35bb37d9a643
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976464"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Přehled aplikačního modelu jazyka Visual Basic

Visual Basic poskytuje dobře definovaný model pro řízení chování aplikací model Windows Forms: Visual Basic aplikační model. Tento model zahrnuje události pro zpracování spuštění a vypnutí aplikace a také události pro zachycení neošetřených výjimek. Poskytuje také podporu pro vývoj aplikací s jednou instancí. Aplikační model je rozšiřitelný, takže vývojáři, kteří potřebují větší ovládací prvek, mohou přizpůsobit své přepsatelné metody.  
  
## <a name="uses-for-the-application-model"></a>Použití pro model aplikace  

 Typická aplikace musí při spuštění a vypnutí provádět úlohy. Například při spuštění aplikace může zobrazit úvodní obrazovku, vytvořit připojení k databázi, načíst uložený stav atd. Když se aplikace ukončí, může zavřít databázová připojení, Uložit aktuální stav atd. Kromě toho může aplikace spustit konkrétní kód, když dojde k neočekávanému ukončení aplikace, například během neošetřené výjimky.  
  
 Model Visual Basic aplikace usnadňuje vytvoření aplikace s *jedinou instancí* . Jedna instance aplikace se liší od normální aplikace, ve které může běžet jenom jedna instance aplikace. Pokus o spuštění jiné instance aplikace s jednou instancí má za následek oznámení původní instance – pomocí `StartupNextInstance` události – tento další pokus o spuštění. Oznámení obsahuje argumenty příkazového řádku další instance. Následná instance aplikace je pak zavřena před tím, než může dojít k inicializaci.  
  
 Spustí se aplikace s jednou instancí a ověří, zda se jedná o první nebo další instanci aplikace:  
  
- Pokud se jedná o první instanci, spustí se obvyklým způsobem.  
  
- Každý následný pokus o spuštění aplikace, zatímco první instance se spustí, má za následek velmi odlišné chování. Následné pokusy upozorní první instanci na argumenty příkazového řádku a okamžitě se ukončí. První instance zpracovává událost `StartupNextInstance`, aby určila, jaké argumenty příkazového řádku následující instance byly, a pokračuje v běhu.  
  
     Tento diagram znázorňuje, jak další instance signalizuje první instanci:  
  
     ![Diagram, který zobrazuje image aplikace s jednou instancí.](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 Zpracováním `StartupNextInstance` události můžete určit, jak se bude aplikace s jednou instancí chovat. Například Microsoft Outlook se obvykle spouští jako aplikace s jedinou instancí; Když je aplikace Outlook spuštěná a pokusíte se znovu spustit aplikaci Outlook, fokus se přesune na původní instanci, ale jiná instance se neotevře.  
  
## <a name="events-in-the-application-model"></a>Události v aplikačním modelu  

 V aplikačním modelu jsou nalezeny následující události:  
  
- **Spuštění aplikace** Aplikace vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> při spuštění. Zpracováním této události můžete přidat kód, který inicializuje aplikaci před načtením hlavního formuláře. Událost `Startup` také umožňuje zrušit provádění aplikace v této fázi procesu spuštění, pokud je to žádoucí.  
  
     Aplikaci můžete nakonfigurovat tak, aby při spuštění spouštěcího kódu aplikace zobrazila úvodní obrazovku. Ve výchozím nastavení model aplikace potlačí úvodní obrazovku při použití argumentu příkazového řádku `/nosplash` nebo `-nosplash`.  
  
- **Aplikace s jednou instancí**. Událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> se vyvolá při spuštění další instance aplikace s jednou instancí. Událost předá argumenty příkazového řádku následující instance.  
  
- **Neošetřené výjimky**. Pokud aplikace narazí na neošetřenou výjimku, vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>. Vaše obslužná rutina pro danou událost může prošetřit výjimku a určit, zda pokračovat v provádění.  
  
     Událost `UnhandledException` se v některých případech nevyvolává. Další informace najdete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>.  
  
- **Změny připojení k síti**. Pokud se změní dostupnost sítě v počítači, aplikace vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
     Událost `NetworkAvailabilityChanged` se v některých případech nevyvolává. Další informace najdete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>.  
  
- **Aplikace byla ukončena**. Aplikace poskytuje událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> k signalizaci, kdy se bude vypínat. V této obslužné rutině události se můžete ujistit, že operace, které vaše aplikace potřebuje, jsou dokončeny a uloženy například. Aplikaci můžete nakonfigurovat tak, aby byla vypnuta, když se zavře hlavní formulář, nebo vypnout pouze v případě, že dojde k zavření všech formulářů.  
  
## <a name="availability"></a>Dostupnost  

 Ve výchozím nastavení je model aplikace Visual Basic k dispozici pro model Windows Forms projekty. Pokud nakonfigurujete aplikaci tak, aby používala jiný spouštěcí objekt, nebo spusťte kód aplikace s vlastním `Sub Main`, může tento objekt nebo třída potřebovat implementaci <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy pro použití aplikačního modelu. Informace o změně spouštěcího objektu naleznete v tématu [Stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
