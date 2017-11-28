---
title: "Závislost oboru názvů My na typu projektu (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a37bf43096931597278974099becb9be6ae133d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Závislost oboru názvů My na typu projektu (Visual Basic)
`My`zpřístupní pouze ty objekty, které jsou vyžadované v určitém projektu typu. Například `My.Forms` objekt je k dispozici v aplikaci Windows Forms, ale není k dispozici v konzolové aplikaci. Toto téma popisuje, které `My` objekty jsou k dispozici v různých typech projektů.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Moje v systému Windows aplikace a webové servery  
 `My`zpřístupní pouze objekty, které jsou užitečné v aktuálním projektu typu. Potlačí objekty, které se nedají použít. Například na následujícím obrázku `My` objektový model v projektu Windows Forms.  
  
 ![Tvar Moje v aplikaci Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 V projektu webu `My` zpřístupní objekty, které jsou relevantní pro webový vývojář (, jako `My.Request` a `My.Response` objekty) při potlačení objekty, které nejsou relevantní (, jako `My.Forms` objekt). Na následujícím obrázku `My` objektový model v projektu webu:  
  
 ![Tvar Moje ve webové aplikaci](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Podrobnosti o projektu  
 Následující tabulka uvádí, které `My` objekty jsou povoleny ve výchozím nastavení pro osm typy projektů: Windows aplikace, třída knihovna, konzolové aplikace, Windows ovládací prvek knihovna, webové ovládací prvek knihovna, Windows služby, prázdný a webový server.  
  
 Existují tři verze `My.Application` objektu, dvě verze `My.Computer` objekt a dvě verze `My.User` objektu; podrobnosti o těchto verzí jsou uvedeny v poznámky pod tabulkou.  
  
|Můj objekt|Aplikace systému Windows|Knihovna tříd|Konzolová aplikace|Knihovna ovládacích prvků Windows|Knihovna webových prvků|Služba systému Windows|prázdný|Webový server|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Ano** <sup>1</sup>|**Ano** <sup>2</sup>|**Ano** <sup>3</sup>|**Ano** <sup>2</sup>|Ne|**Ano** <sup>3</sup>|Ne|Ne|  
|`My.Computer`|**Ano** <sup>4</sup>|**Ano** <sup>4</sup>|**Ano** <sup>4</sup>|**Ano** <sup>4</sup>|**Ano** <sup>5</sup>|**Ano** <sup>4</sup>|Ne|**Ano** <sup>5</sup>|  
|`My.Forms`|**Ano**|Ne|Ne|**Ano**|Ne|Ne|Ne|Ne|  
|`My.Log`|Ne|Ne|Ne|Ne|Ne|Ne|Ne|**Ano**|  
|`My.Request`|Ne|Ne|Ne|Ne|Ne|Ne|Ne|**Ano**|  
|`My.Resources`|**Ano**|**Ano**|**Ano**|**Ano**|**Ano**|**Ano**|Ne|Ne|  
|`My.Response`|Ne|Ne|Ne|Ne|Ne|Ne|Ne|**Ano**|  
|`My.Settings`|**Ano**|**Ano**|**Ano**|**Ano**|**Ano**|**Ano**|Ne|Ne|  
|`My.User`|**Ano** <sup>6</sup>|**Ano** <sup>6</sup>|**Ano** <sup>6</sup>|**Ano** <sup>6</sup>|**Ano** <sup>7</sup>|**Ano** <sup>6</sup>|Ne|**Ano** <sup>7</sup>|  
|`My.WebServices`|**Ano**|**Ano**|**Ano**|**Ano**|**Ano**|**Ano**|Ne|Ne|  
  
 <sup>1</sup> verzi Windows Forms `My.Application`. Je odvozena z verze konzoly (viz poznámka 3); přidává podporu pro interakci s windows aplikace a poskytuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplikačního modelu.  
  
 <sup>2</sup> verzi knihovny `My.Application`. Poskytuje základní funkce potřebné aplikace: poskytuje členové pro zápis do protokolu aplikace a přístup k informacím o aplikaci.  
  
 <sup>3</sup> verzi konzoly `My.Application`. Je odvozena z verze knihovny (viz poznámka 2), a přidá další členy pro přístup k argumenty příkazového řádku a informace o nasazení ClickOnce aplikace.  
  
 <sup>4</sup> verze Windows `My.Computer`. Odvozená z verze serveru (viz poznámku 5) a poskytuje přístup k objektům užitečné na klientský počítač, jako je například klávesnici, obrazovky a myš.  
  
 <sup>5</sup> verzi serveru `My.Computer`. Poskytuje základní informace o počítači, například název, přístup k hodiny a tak dále.  
  
 <sup>6</sup> verze Windows `My.User`. Tento objekt je spojen s aktuální identitou vlákna.  
  
 <sup>7</sup> webové verzi `My.User`. Tento objekt je přidružený ke identita uživatele aplikace aktuální žádost HTTP.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Přizpůsobení výběru objektů jsou k dispozici v mé](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms – objekt](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request – objekt](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response – objekt](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices – objekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
