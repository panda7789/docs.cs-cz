---
title: Závislost oboru názvů My na typu projektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 743160889c4f24a9edb2d0f9799662a74c5061fb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842080"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Závislost oboru názvů My na typu projektu (Visual Basic)
`My` zpřístupní pouze ty objekty, které vyžadují konkrétní typ projektu. Například `My.Forms` objekt je k dispozici v aplikaci Windows Forms, ale není k dispozici v konzolové aplikaci. Toto téma popisuje, které `My` objekty jsou k dispozici v různých typech projektů.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Moje ve Windows aplikací a webů  
 `My` zpřístupňuje pouze objekty, které jsou užitečné v aktuálním typu projektu. Potlačí objekty, které se nedají použít. Například na následujícím obrázku `My` objektového modelu v projektu Windows Forms.  
  
 ![Tvar Moje v aplikaci Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 V projektu webové stránky `My` zpřístupní objekty, které jsou relevantní pro Web developer (, jako `My.Request` a `My.Response` objekty) při potlačení objekty, které nejsou relevantní (například `My.Forms` objekt). Na následujícím obrázku `My` objektového modelu v projektu webové stránky:  
  
 ![Tvar Moje ve webové aplikaci](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Podrobnosti o projektu  
 Následující tabulka uvádí, které `My` objekty jsou povolené ve výchozím nastavení pro osm typů projektů: Aplikace Windows, knihovna tříd, konzolovou aplikaci, Windows Knihovna ovládacích prvků, webové Knihovna ovládacích prvků, Windows služby, prázdná a webové stránky.  
  
 Existují tři verze `My.Application` objektu, dvě verze `My.Computer` objektu a dvě verze `My.User` objektu; podrobnosti o těchto verzích jsou uvedeny v poznámky pod tabulkou.  
  
|Můj objekt|Aplikace Windows|Knihovna tříd|Konzolová aplikace|Knihovna ovládacích prvků Windows|Knihovna webových prvků|Služba systému Windows|prázdný|Webové stránky|  
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
  
 <sup>1</sup> verze Windows Forms `My.Application`. Je odvozen z verze konzoly (viz poznámka 3); přidává podporu pro interakci s vaší aplikace pro windows a poskytuje model aplikace Visual Basic.  
  
 <sup>2</sup> verzi knihovny `My.Application`. Poskytuje základní funkce potřebné aplikace: poskytuje členy pro zápis do protokolu aplikací a přístup k informacím o aplikaci.  
  
 <sup>3</sup> verze konzoly `My.Application`. Je odvozen od verze knihovny (viz poznámka 2), a přidá další členy pro přístup k argumentům příkazového řádku a informace o nasazení ClickOnce vaší aplikace.  
  
 <sup>4</sup> verze Windows `My.Computer`. Je odvozen od verze serveru (viz poznámku 5) a poskytuje přístup na užitečné objekty v klientském počítači, např. klávesnice, obrazovky a myší.  
  
 <sup>5</sup> verze serveru `My.Computer`. Poskytuje základní informace o počítači, jako je jméno, přístup k hodiny a tak dále.  
  
 <sup>6</sup> verze Windows `My.User`. Tento objekt je přidružený aktuální identitu vlákna.  
  
 <sup>7</sup> Webová verze `My.User`. Tento objekt je přidružený identitu uživatele z aktuální žádosti HTTP.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
