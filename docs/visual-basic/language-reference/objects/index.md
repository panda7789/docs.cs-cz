---
title: Objekty (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic]
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61c0967521acda8ac3bf8147b817afcf4ca51165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="objects-visual-basic"></a>Objekty (Visual Basic)
Toto téma obsahuje odkazy na další témata dokument Visual Basic Runtime objekty a obsahovat tabulky jejich člen procedury, vlastnosti a události.  
  
## <a name="visual-basic-run-time-objects"></a>Run-time Visual Basic – objekty  
  
|||  
|---|---|  
|<xref:Microsoft.VisualBasic.Collection>|Představuje pohodlný způsob zobrazíte související skupinu položek, jako jednoho objektu.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Obsahuje informace o běhové chyby.|  
|`My.Application` Objekt se skládá z následujících tříd:<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>poskytuje členy, které jsou k dispozici ve všech projektech.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>poskytuje členy, které jsou k dispozici v aplikacích Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>poskytuje členy, které jsou k dispozici v konzolové aplikace.|Poskytuje data, která souvisí pouze s aktuální aplikace nebo DLL. Žádné informace o úrovni systému může být změněna s `My.Application`.<br /><br /> Někteří členové jsou k dispozici pouze pro Windows Forms nebo konzolové aplikace.|  
|`My.Application.Info` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>)|Poskytuje vlastnosti pro získání informací o aplikaci, například číslo verze, popis, načíst sestavení a tak dále.|  
|`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)|Poskytuje vlastnosti a metody k zápisu událostí a výjimek informace do naslouchací procesy protokolu aplikace.|  
|`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)|Poskytuje vlastnosti pro manipulaci s počítači komponenty, například zvuk, hodiny, klávesnice, systém souborů a tak dále.|  
|`My.Computer.Audio` (<xref:Microsoft.VisualBasic.Devices.Audio>)|Poskytuje metody pro přehrávání zvuku.|  
|`My.Computer.Clipboard` (<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>)|Poskytuje metody pro manipulaci s do schránky.|  
|`My.Computer.Clock` (<xref:Microsoft.VisualBasic.Devices.Clock>)|Poskytuje vlastnosti pro přístup k aktuálním místním časem a světového koordinovaného času (greenwichský střední čas ekvivalent) z systémových hodin.|  
|`My.Computer.FileSystem` (<xref:Microsoft.VisualBasic.FileIO.FileSystem>)|Poskytuje vlastnosti a metody pro práci s disky, souborů a adresářů.|  
|`My.Computer.FileSystem.SpecialDirectories` (<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>)|Poskytuje vlastnosti pro přístup k často odkazuje adresáře.|  
|`My.Computer.Info` (<xref:Microsoft.VisualBasic.Devices.ComputerInfo>)|Poskytuje vlastnosti pro získání informací o paměť, načíst sestavení, název a operační systém počítače.|  
|`My.Computer.Keyboard` (<xref:Microsoft.VisualBasic.Devices.Keyboard>)|Poskytuje vlastnosti pro přístup k aktuální stav klávesnice, jako je například co klíče jsou aktuálně stisknutí a poskytuje metody k odeslání stisknutí kláves do aktivního okna.|  
|`My.Computer.Mouse` (<xref:Microsoft.VisualBasic.Devices.Mouse>)|Poskytuje vlastnosti pro získání informací o formátu a konfiguraci myš, který je nainstalován v místním počítači.|  
|`My.Computer.Network` (<xref:Microsoft.VisualBasic.Devices.Network>)|Poskytuje vlastnosti, události a metody pro interakci s sítě, ke které je připojený počítač.|  
|`My.Computer.Ports` (<xref:Microsoft.VisualBasic.Devices.Ports>)|Poskytuje vlastnosti a metody pro přístup k sériovým portům počítače.|  
|`My.Computer.Registry` (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)|Poskytuje vlastnosti a metody pro práci s registru.|  
|[My.Forms – objekt](../../../visual-basic/language-reference/objects/my-forms-object.md)|Poskytuje vlastnosti pro přístup k instanci jednotlivých formulářů Windows deklarované v aktuálním projektu.|  
|`My.Log` (<xref:Microsoft.VisualBasic.Logging.AspLog>)|Poskytuje vlastnosti a metody pro zápis informací o události a výjimky pro naslouchací procesy pro protokoly aplikace pro webové aplikace.|  
|[My.Request – objekt](../../../visual-basic/language-reference/objects/my-request-object.md)|Získá <xref:System.Web.HttpRequest> objekt pro požadovanou stránku. `My.Request` Objekt obsahuje informace o aktuální žádosti HTTP.<br /><br /> `My.Request` Je k dispozici pouze pro objekt [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace.|  
|[My.Resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md)|Poskytuje třídy a vlastnosti pro přístup k prostředkům aplikace.|  
|[My.Response – objekt](../../../visual-basic/language-reference/objects/my-response-object.md)|Získá <xref:System.Web.HttpResponse> objekt, který je přidružen <xref:System.Web.UI.Page>. Tento objekt umožňuje odeslat data odpovědi HTTP do klienta a obsahuje informace o této odpovědi.<br /><br /> `My.Response` Je k dispozici pouze pro objekt [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] aplikace.|  
|[My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md)|Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.|  
|`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)|Poskytuje přístup k informacím o aktuálním uživateli.|  
|[My.WebServices – objekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Poskytuje vlastnosti pro vytváření a přístup k jediné instance každého webové služby, který se odkazuje v aktuálním projektu.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Poskytuje metody a vlastnosti pro analýza strukturovaných textových souborů.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../../visual-basic/index.md)
