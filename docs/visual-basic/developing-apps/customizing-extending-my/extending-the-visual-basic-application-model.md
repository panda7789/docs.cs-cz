---
title: Rozšíření aplikačního modelu jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 46c18ab540c90c4147514685c2acc824755b435f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976866"
---
# <a name="extending-the-visual-basic-application-model"></a>Rozšíření aplikačního modelu jazyka Visual Basic

Do aplikačního modelu můžete přidat funkce přepsáním `Overridable` členů <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> třídy. Tato technika vám umožní přizpůsobit chování modelu aplikace a přidat volání vlastních metod při spuštění a vypnutí aplikace.

## <a name="visual-overview-of-the-application-model"></a>Vizuální Přehled aplikačního modelu

Tato část vizuálně prezentuje sekvenci volání funkcí v modelu Visual Basic aplikace. V další části se podrobně popisuje účel jednotlivých funkcí.

Následující obrázek znázorňuje sekvenci volání aplikačního modelu v normální Visual Basic model Windows Forms aplikaci. Sekvence začíná, když `Sub Main` procedura volá metodu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

![Diagram znázorňující sekvenci volání aplikačního modelu](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Visual Basic aplikační model poskytuje také události <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> a <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>. Následující obrázek ukazuje mechanismus pro vyvolání těchto událostí.

![Diagram znázorňující metodu OnStartupNextInstance, která vyvolává událost StartupNextInstance.](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![Diagram znázorňující metodu ' UnhandledException ' vyvolávající událost UnhandledException.](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>Přepsání základních metod

Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> definuje pořadí, ve kterém se spouští metody `Application`. Ve výchozím nastavení je `Sub Main` procedura pro model Windows Forms aplikace volána metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A>.

Pokud je aplikace normální aplikací (aplikace s více instancemi) nebo první instancí aplikace s jednou instancí, metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> spouští `Overridable` metody v následujícím pořadí:

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>. Ve výchozím nastavení tato metoda nastaví vizuální styly, styly zobrazení textu a aktuální objekt zabezpečení pro hlavní vlákno aplikace (Pokud aplikace používá ověřování systému Windows) a volá `ShowSplashScreen`, pokud není `/nosplash` ani `-nosplash` použit jako argument příkazového řádku.

     Spouštěcí sekvence aplikace je zrušena, pokud tato funkce vrací `False`. To může být užitečné v případě, že dojde ke situacím, kdy by aplikace neměla běžet.

     Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> volá následující metody:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>. Určuje, zda má aplikace nadefinovanou úvodní obrazovku a v případě jejího zobrazení zobrazí úvodní obrazovku samostatného vlákna.

         Metoda <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> obsahuje kód, který zobrazuje úvodní obrazovku alespoň v počtu milisekund určených vlastností <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>. Chcete-li použít tuto funkci, je nutné přidat úvodní obrazovku do aplikace pomocí **Návrháře projektu** (který nastaví vlastnost `My.Application.MinimumSplashScreenDisplayTime` na dvě sekundy) nebo nastavte vlastnost `My.Application.MinimumSplashScreenDisplayTime` v metodě, která přepíše metodu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> nebo <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Další informace najdete v tématu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>. Umožňuje návrháři vygenerovat kód, který inicializuje úvodní obrazovku.

         Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud vyberete úvodní obrazovku pro aplikaci v **Návrháři projektu**Visual Basic, Návrhář přepíše metodu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> metodou, která nastaví vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> na novou instanci formuláře úvodní obrazovky.

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>. Poskytuje bod rozšiřitelnosti pro vyvolání události `Startup`. Spouštěcí sekvence aplikace se zastaví, pokud tato funkce vrací `False`.

     Ve výchozím nastavení tato metoda vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>. Pokud obslužná rutina události nastaví vlastnost <xref:System.ComponentModel.CancelEventArgs.Cancel> argumentu události na `True`, metoda vrátí `False`, aby se zrušilo spuštění aplikace.

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>. Poskytuje počáteční bod, kdy je hlavní aplikace připravená začít běžet po dokončení inicializace.

     Ve výchozím nastavení před tím, než vstoupí do smyčky zprávy model Windows Forms, tato metoda volá `OnCreateMainForm` (pro vytvoření hlavního formuláře aplikace) a `HideSplashScreen` (pro zavření úvodní obrazovky) metody:

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>. Poskytuje pro návrháře způsob, jak vygenerovat kód, který inicializuje hlavní formulář.

         Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud však vyberete hlavní formulář pro aplikaci v **Návrháři projektu**Visual Basic, Návrhář přepíše metodu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodou, která nastaví vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> na novou instanci hlavního formuláře.

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>. Pokud má aplikace nadefinovanou úvodní obrazovku a je otevřená, tato metoda zavře úvodní obrazovku.

         Ve výchozím nastavení tato metoda zavře úvodní obrazovku.

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>. Poskytuje způsob, jak přizpůsobit způsob, jakým se aplikace s jednou instancí chová při spuštění jiné instance aplikace.

     Ve výchozím nastavení tato metoda vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>.

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>. Poskytuje bod rozšiřitelnosti pro vyvolání události `Shutdown`. Tato metoda se nespustí, pokud dojde k neošetřené výjimce v hlavní aplikaci.

     Ve výchozím nastavení tato metoda vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>.

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>. Provede se, pokud dojde k neošetřené výjimce v některé z výše uvedených metod.

     Ve výchozím nastavení tato metoda vyvolá událost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>, pokud není připojen ladicí program a aplikace zpracovává událost `UnhandledException`.

 Pokud je aplikace jedinou instancí aplikace a aplikace je již spuštěna, další instance aplikace zavolá metodu <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> v původní instanci aplikace a poté ukončí.

 Konstruktor <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> volá vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> a určí, který modul vykreslování textu se má použít pro formuláře aplikace. Ve výchozím nastavení vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> vrací `False`, což značí, že se používá modul vykreslování textu GDI, což je výchozí hodnota v Visual Basic 2005 a novějších verzích. Vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> můžete přepsat tak, aby vracela `True`, což znamená, že se používá modul vykreslování textu GDI+, který je ve výchozím nastavení Visual Basic .NET 2002 a Visual Basic .NET 2003.

## <a name="configuring-the-application"></a>Konfigurace aplikace

 Jako součást modelu Visual Basic aplikace poskytuje třída <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> chráněné vlastnosti, které konfigurují aplikaci. Tyto vlastnosti by měly být nastaveny v konstruktoru implementované třídy.

 Ve výchozím model Windows Forms projektu vytvoří **Návrhář projektu** kód pro nastavení vlastností s nastavením návrháře. Vlastnosti jsou použity pouze v případě, že je aplikace spouštěna; nastavení se po spuštění aplikace nijak neprojeví.

|Vlastnost|Stanoví|Nastavení v podokně aplikace Návrháře projektu|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|Zda je aplikace spuštěna jako aplikace s jednou instancí nebo s více instancemi.|Zaškrtávací políčko **udělat aplikaci s jednou instancí**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|Pokud aplikace bude používat vizuální styly, které odpovídají systému Windows XP.|Zaškrtávací políčko **Povolit vizuální styly XP**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|Pokud aplikace po ukončení aplikace automaticky uloží změny nastavení uživatele aplikace.|Zaškrtávací políčko **Uložit nastavení při vypnutí**|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|To způsobí, že aplikace skončí, například když se zavře formulář při spuštění nebo když se zavře poslední formulář.|Seznam **režimu vypnutí**|

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Přehled aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [Stránka Aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
