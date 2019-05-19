---
title: Objekty (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: 8852a3daa3cd3891d5053cc1fffe19fa310125de
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880724"
---
# <a name="objects-visual-basic"></a>Objekty (Visual Basic)
Toto téma obsahuje odkazy na další témata dokumentu za běhu jazyka Visual Basic objekty a obsahují tabulky jejich člen postupy, vlastnosti a události.  
  
## <a name="visual-basic-run-time-objects"></a>Objektů za běhu jazyka Visual Basic  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Poskytuje pohodlný způsob, jak zobrazit související skupina položek jako jednoho objektu.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Obsahuje informace o chybách za běhu.|  
|`My.Application` Objekt obsahuje následující třídy:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> obsahuje členy, které jsou k dispozici ve všech projektech.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> obsahuje členy nejsou k dispozici v aplikacích Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> obsahuje členy nejsou k dispozici v konzolových aplikacích.|Poskytuje data, která je přidružena pouze aktuální aplikaci nebo knihovny DLL. Žádné informace na úrovni systému můžete změnit pomocí `My.Application`.<br /><br /> Někteří členové jsou dostupné jenom pro Windows Forms a konzolové aplikace.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Poskytuje vlastnosti pro získání informací o aplikaci, jako je třeba číslo verze, popis, načtená sestavení a tak dále.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Poskytuje vlastnosti a metody zapsat informace o události a výjimky do součásti naslouchající protokolům aplikace.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Poskytuje vlastnosti pro práci s počítači komponenty např. zvuk, hodiny, klávesnice, systém souborů a tak dále.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Poskytuje metody pro přehrávání zvuku.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Poskytuje metody pro práci do schránky.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Poskytuje vlastnosti pro přístup k aktuálním místním časem a koordinovaný světový čas (ekvivalent greenwichský střední čas) ze systémových hodin.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Poskytuje vlastnosti a metody pro práci s disky, soubory a adresáře.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Poskytuje vlastnosti pro přístup k často odkazované adresáře.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Poskytuje vlastnosti pro získání informací o paměť, načtená sestavení, název a operační systém počítače.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Poskytuje vlastnosti pro přístup k aktuálním stavu klávesnice, jako je například co klíčů aktuálně stisknutí a představuje způsob, jak odeslat stisknutí kláves do aktivního okna.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Poskytuje vlastnosti pro získání informací o formátu a konfigurace myši, který je nainstalován v místním počítači.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Poskytuje vlastnosti, události a metody pro práci se sítí, ke kterému je počítač připojený.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Poskytuje vlastnosti a metody pro přístup k sériovým portům počítače.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Poskytuje vlastnosti a metody pro práci v registru.|  
|[Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)|Poskytuje vlastnosti pro přístup k instanci jednotlivých formulářů Windows deklaraci v aktuálním projektu.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Poskytuje vlastnosti a metody pro zápis událostí a výjimek informace do součásti naslouchající protokolům aplikace pro webové aplikace.|  
|[Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)|Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku. `My.Request` Objekt obsahuje informace o aktuální žádosti HTTP.<br /><br /> `My.Request` Objekt je k dispozici pouze pro aplikace ASP.NET.|  
|[Objekt My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)|Poskytuje třídy a vlastnosti pro přístup k prostředkům aplikace.|  
|[Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)|Získá <xref:System.Web.HttpResponse> objekt, který je přidružený <xref:System.Web.UI.Page>. Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.<br /><br /> `My.Response` Objekt je k dispozici pouze pro aplikace ASP.NET.|  
|[Objekt My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)|Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Poskytuje přístup k informacím o aktuálním uživateli.|  
|[Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Poskytuje vlastnosti pro vytváření a přístup ke jednu instanci každé webové služby, na který odkazuje aktuální projekt.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Poskytuje metody a vlastnosti pro analýza strukturovaných textových souborů.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
- [Visual Basic](../../../visual-basic/index.md)
