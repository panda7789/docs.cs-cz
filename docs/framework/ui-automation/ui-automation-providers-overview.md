---
title: Přehled zprostředkovatelů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 1f780ffc37b0aff93a3358c1980d271fe10c1321
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179880"
---
# <a name="ui-automation-providers-overview"></a>Přehled zprostředkovatelů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Zprostředkovatelé automatizace uživatelského rozhraní umožňují ovládacím prvkům komunikovat s klientskými aplikacemi automatizace uživatelského rozhraní. Obecně platí, že každý ovládací [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] prvek nebo jiný odlišný prvek v a je reprezentován zprostředkovatelem. Zprostředkovatel zveřejňuje informace o prvku a volitelně implementuje vzory ovládacích prvků, které umožňují klientské aplikaci pracovat s ovládacím prvkem.  
  
 Klientské aplikace obvykle nemusí pracovat přímo s poskytovateli. Většina standardních ovládacích prvků v aplikacích, které [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] používají Win32, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Windows Forms nebo architektury jsou automaticky vystaveny systému. Aplikace, které implementují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastní ovládací prvky, mohou také implementovat zprostředkovatele pro tyto ovládací prvky a klientské aplikace nemusí provádět žádné zvláštní kroky k získání přístupu k nim.  
  
 Toto téma obsahuje přehled o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tom, jak vývojáři ovládacích prvků implementují zprostředkovatele, zejména pro ovládací prvky ve Windows Forms a Win32 windows.  
  
<a name="Types_of_Providers"></a>
## <a name="types-of-providers"></a>Typy poskytovatelů  
 Zprostředkovatelé automatizace uživatelského rozhraní spadají do dvou kategorií: zprostředkovatelé na straně klienta a zprostředkovatelé na straně serveru.  
  
### <a name="client-side-providers"></a>Poskytovatelé na straně klienta  
 Zprostředkovatelé na straně klienta jsou implementovány klienty Automatizace uživatelského rozhraní ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]komunikaci s aplikací, která nepodporuje nebo plně nepodporuje . Zprostředkovatelé na straně klienta obvykle komunikují se serverem přes hranice procesu odesíláním a přijímáním zpráv systému Windows.  
  
 Vzhledem k tomu, že zprostředkovatelé automatizace [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] uživatelského rozhraní pro ovládací prvky v systému Win32, Windows Forms nebo aplikací jsou dodávány jako součást operačního systému, klientské aplikace zřídka mají implementovat své vlastní zprostředkovatele a tento přehled nepokrývá je dále.  
  
### <a name="server-side-providers"></a>Zprostředkovatelé na straně serveru  
 Zprostředkovatelé na straně serveru jsou implementováni vlastními ovládacími prvky nebo aplikacemi, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]které jsou založeny na jiném rámci rozhraní ui než Win32, Windows Forms nebo .  
  
 Zprostředkovatelé na straně serveru komunikují s klientskými aplikacemi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] přes hranice procesu tím, že vystavují rozhraní základnímu systému, který zase obsluhuje požadavky klientů.  
  
<a name="AutomationProviderConcepts"></a>
## <a name="ui-automation-provider-concepts"></a>Koncepty zprostředkovatelů automatizace uživatelského rozhraní  
 Tato část obsahuje stručné vysvětlení některých klíčových konceptů, které je třeba pochopit, aby bylo možné implementovat zprostředkovatele automatizace uživatelského rozhraní.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]prvky jsou [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] kusy, které jsou viditelné pro klienty automatizace uživatelského rozhraní. Mezi příklady patří okna aplikací, podokna, tlačítka, popisky, seznamy a položky seznamu.  
  
### <a name="navigation"></a>Navigace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]prvky jsou klientům [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vystaveny jako strom. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]vytvoří strom přechodem z jednoho prvku do druhého. Navigace je povolena zprostředkovateli pro každý prvek, z nichž každý může překážet na nadřazené, na stejné úrovni a podřízené objekty.  
  
 Další informace o zobrazení klienta ve stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] naleznete v [tématu Přehled automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Zobrazení  
 Klient může zobrazit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom ve třech hlavních zobrazeních, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Nezpracovaná zobrazení|Obsahuje všechny prvky.|  
|Zobrazení ovládacího prvku|Obsahuje prvky, které jsou ovládací prvky.|  
|Zobrazení obsahu|Obsahuje prvky, které mají obsah.|  
  
 Další informace o klientských [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazeních stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
 Je odpovědností implementace zprostředkovatele definovat prvek jako prvek obsahu nebo prvek ovládacího prvku. Ovládací prvky mohou nebo nemusí být také prvky obsahu, ale všechny prvky obsahu jsou prvky ovládacího prvku.  
  
### <a name="frameworks"></a>Rozhraní  
 Rozhraní framework je součást, která spravuje podřízené ovládací prvky, testování přístupů a vykreslování v oblasti obrazovky. Například okno Win32, často označované jako HWND, může sloužit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jako rámec, který obsahuje více prvků, jako je například řádek nabídek, stavový řádek a tlačítka.  
  
 Ovládací prvky kontejneru Win32, jako jsou seznamy a stromová zobrazení jsou považovány za rámce, protože obsahují vlastní kód pro vykreslování podřízených položek a provádění testování přístupů na nich. Naproti tomu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] seznam není rámec, protože vykreslování a testování [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] přístupů je zpracováváno obsahující okno.  
  
 V [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplikaci mohou být tvořeny různými rámci. Okno aplikace HWND může například obsahovat dynamické HTML (DHTML), které zase obsahuje komponentu, jako je například pole se seznamem v HWND.  
  
### <a name="fragments"></a>Fragments  
 Fragment je úplný podstrom prvků z určitého rámce. Prvek v kořenovém uzlu podstromu se nazývá kořen ový fragment. Kořen fragmentu nemá nadřazený, ale je hostován v rámci jiného rámce, obvykle okno Win32 (HWND).  
  
### <a name="hosts"></a>Hostitelé  
 Kořenový uzel každého fragmentu musí být hostován v elementu, obvykle v okně Win32 (HWND). Výjimkou je plocha, která není hostována v žádném jiném prvku. Hostitel vlastní ovládací prvek je HWND samotného ovládacího prvku, nikoli okno aplikace nebo jiné okno, které může obsahovat skupiny ovládacích prvků nejvyšší úrovně.  
  
 Hostitel fragmentu hraje důležitou roli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] při poskytování služeb. Umožňuje navigaci do kořenového adresáře fragmentu a poskytuje některé výchozí vlastnosti tak, aby je vlastní zprostředkovatel nemusel implementovat.  
  
## <a name="see-also"></a>Viz také

- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
