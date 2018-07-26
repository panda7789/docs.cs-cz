---
title: Rozšíření aplikačního modelu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 64c175216cf21b7947462cf79e4b88ab6fcd6d86
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245645"
---
# <a name="extending-the-visual-basic-application-model"></a>Rozšíření aplikačního modelu jazyka Visual Basic
Funkce můžete přidat do modelu aplikace tak, že přepíšete `Overridable` členy <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy. Tato technika umožňuje přizpůsobit chování aplikační model a přidávat volání vlastní metody aplikace po spuštění a ukončení.  
  
## <a name="visual-overview-of-the-application-model"></a>Vizuální přehled aplikačního modelu  
 Tato část představuje vizuálně pořadí volání funkcí v aplikačního modelu jazyka Visual Basic. Další část popisuje účel jednotlivých funkcí v podrobností.  
  
 Následující obrázek znázorňuje sekvenci volání aplikačního modelu v normální aplikaci Windows Forms jazyka Visual Basic. Sekvence začíná, když `Sub Main` volání procedur <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody.  
  
 ![Aplikační Model Visual Basic &#45; &#45; spustit](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB_ModelRun")  
  
 Také poskytuje aplikačního modelu jazyka Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> události. Následující obrázky znázorňují mechanismus pro vyvolání těchto událostí.  
  
 ![Aplikační Model Visual Basic &#45; &#45; další Instance](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB_ModelNext")  
  
 ![Neošetřená výjimka aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB_UnhandEx")  
  
## <a name="overriding-the-base-methods"></a>Přepisování základních metod  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> Metoda definuje pořadí, ve kterém `Application` metody spouštění. Ve výchozím nastavení `Sub Main` volání procedur pro aplikace Windows Forms <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody.  
  
 Pokud aplikace je běžné aplikace (více instancí aplikace), nebo první výskyt aplikace s jedinou instancí, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> metody `Overridable` metod v tomto pořadí:  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Ve výchozím nastavení, tato metoda nastaví vizuálních stylů, styly zobrazení textu a aktuální objekt zabezpečení pro hlavního vlákna aplikace (Pokud aplikace používá ověřování Windows) a volání `ShowSplashScreen` Pokud `/nosplash` ani `-nosplash` slouží jako argument příkazového řádku.  
  
     Sekvence spuštění aplikace se zruší, pokud tato funkce vrací `False`. To může být užitečné, pokud existují okolnosti, ve kterých není vhodné spouštět aplikace.  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> Metoda volání těchto metod:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Určuje, zda má aplikace úvodní obrazovku a pokud ano, zobrazí na úvodní obrazovce na samostatném vlákně.  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> Metoda obsahuje kód, který se zobrazí úvodní obrazovky pro minimální počet milisekund, které jsou určené <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> vlastnost. Tuto funkci použít, je nutné přidat úvodní obrazovky do aplikace pomocí **Návrháře projektu** (který nastaví `My.Application.MinimumSplashScreenDisplayTime` vlastnost na dvou sekund), nebo nastavte `My.Application.MinimumSplashScreenDisplayTime` vlastnost v metodě, která přepíše <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> nebo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metody. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Umožňuje generovat kód, který se inicializuje na úvodní obrazovce designeru.  
  
         Ve výchozím nastavení tato metoda nemá žádný účinek. Pokud vyberete úvodní obrazovka pro vaši aplikaci v jazyce Visual Basic **Návrháře projektu**, přepíše návrháře <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metodu s metodou, která nastavuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> vlastnost do nové instance formuláře úvodní obrazovky .  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Představuje rozšíření bod pro vyvolání `Startup` událostí. Sekvence spuštění aplikace se zastaví, pokud tato funkce vrací `False`.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> událostí. Pokud je obslužná rutina události nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel> vlastnosti argumentu události `True`, metoda vrátí `False` zrušit spuštění aplikace.  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Poskytuje výchozí bod pro aplikace v hlavní aplikaci jste připravení začít spouštět po dokončení inicializace.  
  
     Ve výchozím nastavení, aby přešel do smyčky zpráv Windows Forms, tato metoda volá `OnCreateMainForm` (Chcete-li vytvořit hlavní formulář aplikace) a `HideSplashScreen` (pro zavření úvodní obrazovky) metody:  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Poskytuje způsob pro návrháře a vygenerovat kód, který inicializuje hlavního formuláře.  
  
         Ve výchozím nastavení tato metoda nemá žádný účinek. Nicméně, když vyberete hlavní formulář pro vaši aplikaci v jazyce Visual Basic **Návrháře projektu**, přepíše návrháře <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodu s metodou, která nastavuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> vlastnost na novou instanci třídy hlavního formuláře.  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Pokud má aplikace úvodní obrazovku a je otevřen, tato metoda se zavře úvodní obrazovka.  
  
         Ve výchozím nastavení tato metoda se zavře úvodní obrazovka.  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Poskytuje způsob, jak přizpůsobit chování aplikace s jedinou instancí při spuštění jiná instance aplikace.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> událostí.  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Představuje rozšíření bod pro vyvolání `Shutdown` událostí. Tato metoda se nespustí, pokud dojde k neošetřené výjimce v hlavní aplikaci.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> událostí.  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Provede, pokud dojde k neošetřené výjimce v některém z výše uvedených metod.  
  
     Ve výchozím nastavení, tato metoda vyvolá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> , dokud není připojen ladicí program a aplikace zpracovává události `UnhandledException` událostí.  
  
 Pokud je aplikace s jedinou instancí aplikace a aplikace je již spuštěna, další instance aplikace volá <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> metodu na původní instanci aplikace, a poté ukončí.  
 
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> Volání konstruktoru <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> a určí, které vykreslovací jádro text pro formuláře aplikace. Ve výchozím nastavení <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> vrátí vlastnost `False`, označující, že se text vykreslovací modul GDI používat, což je výchozí hodnota v [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)]. Je možné přepsat <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> vlastnost vrátit `True`, což znamená, že text vykreslovací modul GDI + používat, což je výchozí hodnotou v jazyce Visual Basic .NET 2002 a Visual Basic .NET 2003.  
  
## <a name="configuring-the-application"></a>Konfigurace aplikace  
 Jako součást modelu aplikace Visual Basic <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering> třída poskytuje chráněné vlastnosti, které konfigurace aplikace. Tyto vlastnosti musí být nastaveno v konstruktoru implementující třídu.  
  
 V projektu Windows Forms výchozí **Návrháře projektu** vytvoří kód pro nastavení vlastnosti pomocí Návrháře nastavení. Vlastnosti se používají pouze v případě, že se spouští aplikace; nastavit je po spuštění aplikace nemá žádný vliv.  
  
|Vlastnost|Určuje|Nastavení v podokně aplikace Návrháře projektu|  
|---|---|---|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Určuje, zda aplikace běží jako instance jednoho nebo více instancemi aplikace.|**Ujistěte se, jedna instance aplikace** zaškrtávací políčko|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Pokud bude aplikace používat vizuální styly, které odpovídají Windows XP.|**Povolení vizuálních stylů XP** zaškrtávací políčko|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Pokud aplikaci automaticky uloží změny nastavení uživatele vaší aplikace při ukončení aplikace.|**Při vypnutí ukládání My.Settings** zaškrtávací políčko|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|Co způsobí, že je aplikace ukončena, třeba když se zavře úvodní formulář nebo když se zavře poslední formulář.|**Ukončení režimu** seznamu|  
  
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
