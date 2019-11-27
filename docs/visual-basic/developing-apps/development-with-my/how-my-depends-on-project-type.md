---
title: Závislost oboru názvů My na typu projektu
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 975b8feb001bcab22185be0a360b0512de099b79
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330270"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Závislost oboru názvů My na typu projektu (Visual Basic)

`My` zpřístupňuje pouze objekty, které jsou vyžadovány konkrétním typem projektu. Například objekt `My.Forms` je k dispozici v aplikaci model Windows Forms, ale není k dispozici v konzolové aplikaci. Toto téma popisuje, které `My` objekty jsou k dispozici v různých typech projektů.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>My v aplikacích a webech Windows  

 `My` zveřejňuje pouze objekty, které jsou užitečné v aktuálním typu projektu. potlačí objekty, které nejsou k dispozici. Například následující obrázek ukazuje model objektu `My` v projektu model Windows Forms.  
  
 ![Diagram, který zobrazuje model My Object ve model Windows Forms aplikaci.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 V projektu webu `My` zveřejňuje objekty, které jsou relevantní pro webový vývojář (například objekty `My.Request` a `My.Response`) při potlačení objektů, které nejsou relevantní (například objekt `My.Forms`). Na následujícím obrázku je znázorněn objektový model `My` v projektu webu:  
  
 ![Diagram, který zobrazuje objektový model ve webové aplikaci.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Podrobnosti o projektu  

 Následující tabulka ukazuje, které `My` objekty jsou standardně povoleny pro osm typů projektů: aplikace systému Windows, knihovna tříd, konzolová aplikace, knihovna ovládacích prvků systému Windows, knihovna webového ovládacího prvku, služba systému Windows, prázdná a webový server.  
  
 Existují tři verze objektu `My.Application`, dvě verze objektu `My.Computer` a dvě verze objektu `My.User`; Podrobnosti o těchto verzích jsou uvedeny v poznámkách pod čarou po tabulce.  
  
|Můj objekt|Aplikace systému Windows|Knihovna tříd|Konzolová aplikace|Knihovna ovládacích prvků Windows|Knihovna webového ovládacího prvku|Služba systému Windows|Prázdné|Web|  
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
  
 <sup>1</sup> model Windows Forms verze `My.Application`. Je odvozena z verze konzoly nástroje (viz poznámku 3); přidává podporu pro interakci s okny aplikace a poskytuje model aplikace Visual Basic.  
  
 <sup>2</sup> `My.Application`knihovny. Poskytuje základní funkce, které vyžaduje aplikace: poskytuje členům zápis do aplikačního protokolu a přístup k informacím o aplikaci.  
  
 <sup>3</sup> `My.Application`verze konzoly Je odvozena z verze knihovny (viz poznámku 2) a přidává další členy pro přístup k argumentům příkazového řádku aplikace a k informacím o nasazení ClickOnce.  
  
 <sup>4</sup> `My.Computer`verze Windows Je odvozena z verze serveru (viz poznámku 5) a poskytuje přístup k užitečným objektům v klientském počítači, jako jsou klávesnice, obrazovka a myš.  
  
 <sup>5</sup> `My.Computer`verze serveru. Poskytuje základní informace o počítači, jako je třeba název, přístup k hodinám a tak dále.  
  
 <sup>6</sup> `My.User`verze Windows Tento objekt je přidružen k aktuální identitě vlákna.  
  
 <sup>7</sup> webová verze `My.User`. Tento objekt je přidružený k identitě uživatele aktuálního požadavku HTTP aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objekt My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objekt My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objekt My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objekt My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
