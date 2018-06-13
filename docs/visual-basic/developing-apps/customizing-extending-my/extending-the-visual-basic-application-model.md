---
title: Rozšíření aplikačního modelu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 64c175216cf21b7947462cf79e4b88ab6fcd6d86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591869"
---
# <a name="extending-the-visual-basic-application-model"></a>Rozšíření aplikačního modelu jazyka Visual Basic
Funkce můžete přidat do aplikačního modelu přepsáním `Overridable` členy <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy. Tento postup umožňuje přizpůsobit chování aplikačního modelu služby a přidejte volání vlastní metody aplikace po spuštění a vypnutí.  
  
## <a name="visual-overview-of-the-application-model"></a>Vizuální přehled aplikačního modelu služby  
 Tato část vizuálně představuje sekvenci volání funkce v aplikační Model Visual Basic. Další část popisuje účel podrobně každou funkci.  
  
 Následující obrázek zobrazuje posloupnost volání modelu aplikace ve normální aplikace Windows Forms jazyka Visual Basic. Spustí sekvenci, kdy `Sub Main` volání procedur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metoda.  
  
 ![Aplikační Model Visual Basic &#45; &#45; spustit](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB_ModelRun")  
  
 Aplikační Model Visual Basic také poskytuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> události. Následující obrázky znázorňují, tento mechanismus pro vyvolání těchto událostí.  
  
 ![Aplikační Model Visual Basic &#45; &#45; další Instance](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB_ModelNext")  
  
 ![Aplikační Model Visual Basic neošetřená výjimka](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB_UnhandEx")  
  
## <a name="overriding-the-base-methods"></a>Přepisování základních metod  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Metoda definuje pořadí, ve kterém `Application` metody spustit. Ve výchozím nastavení `Sub Main` volání procedury pro aplikaci Windows Forms <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metoda.  
  
 Pokud aplikace je běžné aplikace (více instancí aplikace), nebo první instance jednoduchou aplikaci, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody `Overridable` metody v následujícím pořadí:  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Ve výchozím nastavení, tato metoda nastaví vizuální styly, styly zobrazení textu a aktuální objekt zabezpečení pro hlavní vlákno aplikace (Pokud aplikace používá ověřování systému Windows) a volání `ShowSplashScreen` Pokud `/nosplash` ani `-nosplash` slouží jako argument příkazového řádku.  
  
     Spouštění aplikace se zruší, pokud funkce vrátí hodnotu `False`. To může být užitečné, pokud existují okolnosti, ve kterých není doporučeno spouštět aplikace.  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Metoda volá následující metody:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Určuje, zda má aplikace úvodní obrazovku a pokud ano, zobrazí úvodní obrazovka na samostatné vlákno.  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Metoda obsahuje kód, který se zobrazí úvodní obrazovku alespoň počet milisekund, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> vlastnost. Chcete-li používat tuto funkci, je nutné přidat úvodní obrazovka k aplikaci pomocí **Návrhář projektu** (které nastaví `My.Application.MinimumSplashScreenDisplayTime` vlastnost, která má dvě sekundy), nebo nastavte `My.Application.MinimumSplashScreenDisplayTime` vlastnost metodu, která přepisuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> nebo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metoda. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Umožňuje designeru vyvolat kód, který inicializuje úvodní obrazovka.  
  
         Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud vyberete úvodní obrazovka pro aplikace v jazyce Visual Basic **Návrhář projektu**, přepíše návrháře <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metodu se metoda, která nastaví <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> vlastnost do nové instance formuláře úvodní obrazovky .  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Poskytuje bod rozšiřitelnosti pro vyvolání `Startup` událostí. Spouštění aplikace zastaví, pokud funkce vrátí hodnotu `False`.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí. Pokud je nastaví obslužné rutiny události <xref:System.ComponentModel.CancelEventArgs.Cancel> vlastnost argument události `True`, vrátí metoda `False` zrušit spuštění aplikace.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Poskytuje výchozí bod pro při hlavní aplikace je připravena k začít spouštět po dokončení inicializace.  
  
     Ve výchozím nastavení, aby přešel do Windows Forms zpráva smyčky, tato metoda volá `OnCreateMainForm` (Chcete-li vytvořit hlavní formulář aplikace) a `HideSplashScreen` (ukončíte úvodní obrazovka) metody:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Poskytuje způsob, jak návrháře pro vydávání kód, který inicializuje hlavní formulář.  
  
         Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud však vyberete hlavní formulář pro vaši aplikaci v jazyce Visual Basic **Návrhář projektu**, přepíše návrháře <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodu se metoda, která nastaví <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> vlastnost novou instanci třídy hlavní formulář.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Pokud má aplikace úvodní obrazovku a je otevřené, tato metoda zavře úvodní obrazovka.  
  
         Ve výchozím nastavení tato metoda zavře úvodní obrazovka.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Poskytuje způsob, jak přizpůsobit chování aplikace s jedinou instancí při spuštění jiná instance aplikace.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> událostí.  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Poskytuje bod rozšiřitelnosti pro vyvolání `Shutdown` událostí. Tato metoda se nespustí, pokud dojde k neošetřené výjimce v hlavní aplikaci.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událostí.  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Provést, pokud dojde k neošetřené výjimce v některém z výše uvedených metod.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> , pokud není připojen ladicí program a aplikace zpracovává události `UnhandledException` událostí.  
  
 Pokud je aplikace s jedinou instancí aplikace a aplikace je již spuštěna, zavolá další instance aplikace <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> metodu na původní instanci systému aplikace a pak se ukončí.  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Volá konstruktor <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> vlastnost, která má-li určit, které modul vykreslování textu pro formulářů aplikace. Ve výchozím nastavení <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> vlastnost vrátí `False`, která udává, že modul vykreslování textu GDI používat, což je výchozí hodnota v [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Je možné přepsat <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> vlastnost vrátit `True`, což naznačuje, že se modul vykreslování textu GDI + používat, což je výchozí hodnota v jazyce Visual Basic .NET 2002 a Visual Basic .NET 2003.  
  
## <a name="configuring-the-application"></a>Konfigurace aplikace  
 Jako součást modelu aplikace Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> třída poskytuje chráněné vlastnosti, které konfigurace aplikace. Tyto vlastnosti musí být nastaveno v konstruktoru implementující třídu.  
  
 Ve Windows Forms výchozí projekt **Návrhář projektu** vytvoří kód a nastavte vlastnosti návrháře nastavení. Vlastnosti se používá jenom v případě, že se spouští aplikace; nastavení je po spuštění aplikace nemá žádný vliv.  
  
|Vlastnost|Určuje|Nastavení v podokně aplikace v Návrháři projektu|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Jestli je aplikace spuštěná jako instance jednoho nebo více instancí aplikace.|**Ujistěte se, jedna instance aplikace** zaškrtávací políčko|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Pokud aplikace bude používat vizuální styly, které odpovídají Windows XP.|**Povolit vizuální styly XP** zaškrtávací políčko|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Pokud aplikace automaticky uloží změny nastavení uživatele aplikace při ukončení aplikace.|**Uložit My.Settings na vypnutí** zaškrtávací políčko|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Co způsobí, že je aplikace ukončena, například při zavření formuláře spuštění nebo při zavření posledního formuláře.|**Vypnutí režimu** seznamu|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 [Přehled aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
