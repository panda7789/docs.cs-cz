---
title: Přehled zprostředkovatelů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: e48e2eb0df8fbc4daf4db68b0c27493b122adfa3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-providers-overview"></a>Přehled zprostředkovatelů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Zprostředkovatelé automatizace uživatelského rozhraní povolit ovládací prvky pro komunikaci s automatizace uživatelského rozhraní klientské aplikace. V obecné, každý ovládací prvek nebo jiného odlišné elementu v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] je reprezentována zprostředkovatele. Zprostředkovatel zveřejňuje informace o elementu a volitelně implementuje vzory ovládacích prvků, které umožňují klientskou aplikaci pro interakci s ovládacím prvkem.  
  
 Klientské aplikace obvykle nemají pracovat přímo s zprostředkovatele. Většina standardní ovládací prvky v aplikacích, které používají [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], nebo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] architektury jsou automaticky vystavený [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systému. Aplikace, které implementují vlastní ovládací prvky může také implementovat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zprostředkovatelé pro tyto ovládací prvky a klientské aplikace není nutné žádné speciální kroky k získání přístupu k nim.  
  
 Toto téma obsahuje základní informace o tom, jak implementovat vývojáři ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelů, zejména pro ovládací prvky v [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] systému windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy poskytovatelů  
 Zprostředkovatelé automatizace uživatelského rozhraní lze rozdělit do dvou kategorií: zprostředkovatele na straně klienta a zprostředkovatele na straně serveru.  
  
### <a name="client-side-providers"></a>Zprostředkovatelé na straně klienta  
 Klientské poskytovatelé se implementují klienty automatizace uživatelského rozhraní pro komunikaci s aplikací, která nepodporuje, nebo plně nepodporuje, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Zprostředkovatelé na straně klienta obvykle komunikaci se serverem přes hranice procesu přijatých a odeslaných zpráv systému Windows.  
  
 Protože zprostředkovatelů automatizace uživatelského rozhraní pro ovládací prvky v [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikace jsou zadaná jako součást operačního systému, klientských aplikací mít málokdy k implementaci vlastních poskytovatelů a tento přehled je nepokrývá Další.  
  
### <a name="server-side-providers"></a>Zprostředkovatelé na straně serveru  
 Serverové poskytovatelé se implementují vlastní ovládací prvky nebo aplikace, které jsou založeny na rozhraní uživatelského rozhraní, jiné než [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Zprostředkovatele na straně serveru komunikovat s klientským aplikacím přes hranice procesu díky zpřístupnění rozhraní, které se [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] základní systém, který naopak obsluhuje požadavky od klientů.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Koncepty zprostředkovatele automatizace uživatelského rozhraní  
 Tato část nabízí stručné vysvětlení některých klíčových konceptů, které je třeba pochopit, aby bylo možné implementace zprostředkovatele automatizace uživatelského rozhraní.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy jsou části [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , které jsou viditelné pro klienty automatizace uživatelského rozhraní. Mezi příklady patří aplikace windows, podokna, tlačítek, popisy tlačítek, seznamy a položky seznamu.  
  
### <a name="navigation"></a>Navigace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy jsou umístěny do klientů jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vytvoří stromu tak, že přejdete od jednoho prvku na jiný. Zprostředkovatelé pro každý element, z nichž každá může přejděte na nadřazený, jsou na stejné úrovni a podřízené položky je povolena navigace.  
  
 Další informace o zobrazení klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>zobrazení  
 Klienta můžete zobrazit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu v tři hlavní zobrazení, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Nezpracovaná zobrazení|Obsahuje všechny elementy.|  
|Zobrazení ovládacího prvku|Obsahuje prvky, které jsou ovládací prvky.|  
|Zobrazení obsahu|Obsahuje prvky, které mají obsah.|  
  
 Další informace o zobrazení klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Je zodpovědností implementace zprostředkovatele definujte element jako element obsahu nebo elementu ovládacího prvku. Ovládací prvky může nebo nemusí být také obsahu elementů, ale všechny obsahu prvky jsou ovládací prvky.  
  
### <a name="frameworks"></a>rozhraní  
 Rozhraní je komponenta, která spravuje podřízených ovládacích prvků, stiskněte klávesu testování a jsou vykreslení v oblasti obrazovky. Například [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okno, které se často označuje jako popisovačem HWND může sloužit jako rozhraní, která obsahuje více [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementy například řádku nabídek, stavového řádku a tlačítka.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontejner řídí například seznamy a zobrazení stromu se považují za rozhraní, protože obsahují vlastní kód pro vykreslování podřízené položky a provádění vstupů do testování na ně. Naopak [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pole se seznamem není rozhraní, protože vykreslování a stiskněte klávesu testování je zpracovanou obsahující [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] okno.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] v aplikaci může být tvořen různé architektury. Například může obsahovat okna aplikace HWND [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] který zase obsahuje součásti, např. pole se seznamem v popisovačem HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Fragment je podstromu prvků z konkrétní rozhraní. Element v kořenového uzlu podstromu nazývá kořenové fragment. Fragment kořenové nemá nadřazený, ale je obvykle hostovaným v rámci jiné framework, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] okno (HWND).  
  
### <a name="hosts"></a>Hostitelé  
 Kořenový uzel každý fragment musí být hostované v elementu, obvykle [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okno (HWND). Výjimkou je plochy, kterou není hostovaný v jiného elementu. Je hostitel vlastního ovládacího prvku HWND samotného ovládacího prvku, není okno aplikace nebo jakékoli jiné okno, které může obsahovat skupin nejvyšší úrovně ovládacích prvků.  
  
 Hostitele fragment hraje důležitou roli při poskytování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služeb. Umožňuje navigace do kořenového adresáře fragment a poskytuje některé výchozí vlastnosti tak, aby vlastní zprostředkovatel nemá pro jejich implementaci.  
  
## <a name="see-also"></a>Viz také  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
