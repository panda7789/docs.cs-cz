---
title: Objekty
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
ms.openlocfilehash: 2108e36956ada98e48e6ab05cec56dbf2a12b3dd
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838257"
---
# <a name="objects-visual-basic"></a>Objekty (Visual Basic)
Toto téma obsahuje odkazy na další témata, která dokumentují Visual Basic objekty modulu runtime a obsahují tabulky jejich členských procedur, vlastností a událostí.  
  
## <a name="visual-basic-run-time-objects"></a>Visual Basic běhových objektů  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Poskytuje pohodlný způsob, jak zobrazit související skupinu položek jako jeden objekt.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Obsahuje informace o chybách za běhu.|  
|Objekt `My.Application` se skládá z následujících tříd:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> poskytuje členy, kteří jsou k dispozici ve všech projektech.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> poskytuje členy, které jsou k dispozici v model Windows Forms aplikacích.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> poskytuje členy, kteří jsou k dispozici v konzolových aplikacích.|Poskytuje data, která jsou přidružena pouze k aktuální aplikaci nebo knihovně DLL. Pomocí `My.Application`nelze změnit žádné informace na úrovni systému.<br /><br /> Někteří členové jsou k dispozici pouze pro model Windows Forms nebo konzolové aplikace.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Poskytuje vlastnosti pro získání informací o aplikaci, jako je číslo verze, popis, načtená sestavení a tak dále.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Poskytuje vlastnost a metody pro zápis informací o událostech a výjimkách do protokolu naslouchacího procesu aplikace.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Poskytuje vlastnosti pro manipulaci s součástmi počítače, jako jsou zvuk, hodiny, klávesnice, systém souborů a tak dále.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Poskytuje metody pro přehrávání zvuků.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Poskytuje metody pro manipulaci se schránkou.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Poskytuje vlastnosti pro přístup k aktuálnímu místnímu času a univerzálnímu koordinovanému času (ekvivalentnímu střednímu času) ze systémových hodin.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Poskytuje vlastnosti a metody pro práci s jednotkami, soubory a adresáři.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Poskytuje vlastnosti pro přístup k často odkazovaným adresářům.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Poskytuje vlastnosti pro získání informací o paměti počítače, načtených sestavení, názvu a operačním systému.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Poskytuje vlastnosti pro přístup k aktuálnímu stavu klávesnice, jako jsou aktuálně stisknuté klávesy, a poskytuje metodu pro posílání kláves do aktivního okna.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Poskytuje vlastnosti pro získání informací o formátu a konfiguraci myši, která je nainstalována v místním počítači.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Poskytuje vlastnost, událost a metody pro komunikaci se sítí, ke které je počítač připojený.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Poskytuje vlastnost a metodu pro přístup k sériovým portům počítače.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Poskytuje vlastnosti a metody pro manipulaci s registrem.|  
|[Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)|Poskytuje vlastnosti pro přístup k instanci každého formuláře Windows deklarovaného v aktuálním projektu.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Poskytuje vlastnost a metody pro zápis informací o událostech a výjimkách do aplikačních posluchačů protokolů pro webové aplikace.|  
|[Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)|Získá objekt <xref:System.Web.HttpRequest> pro požadovanou stránku. Objekt `My.Request` obsahuje informace o aktuálním požadavku HTTP.<br /><br /> Objekt `My.Request` je k dispozici pouze pro aplikace ASP.NET.|  
|[Objekt My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)|Poskytuje vlastnosti a třídy pro přístup k prostředkům aplikace.|  
|[Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)|Získá objekt <xref:System.Web.HttpResponse>, který je spojen s <xref:System.Web.UI.Page>. Tento objekt umožňuje odeslat data odpovědi HTTP klientovi a obsahuje informace o této odpovědi.<br /><br /> Objekt `My.Response` je k dispozici pouze pro aplikace ASP.NET.|  
|[Objekt My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)|Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Poskytuje přístup k informacím o aktuálním uživateli.|  
|[Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Poskytuje vlastnosti pro vytvoření a přístup k jedné instanci každé webové služby, na kterou se odkazuje aktuální projekt.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Poskytuje metody a vlastnosti pro analýzu strukturovaných textových souborů.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
