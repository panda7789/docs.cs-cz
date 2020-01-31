---
title: Přehled zprostředkovatelů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 98208f1e1fa1b540bf3880e33478854128505233
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778786"
---
# <a name="ui-automation-providers-overview"></a>Přehled zprostředkovatelů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Zprostředkovatelé automatizace uživatelského rozhraní umožňují ovládacím prvkům komunikovat s klientskými aplikacemi pro automatizaci uživatelského rozhraní. Obecně platí, že každý ovládací prvek nebo jiný jedinečný prvek v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] představuje poskytovatel. Zprostředkovatel zpřístupňuje informace o elementu a volitelně implementuje vzory ovládacích prvků, které umožňují klientské aplikaci pracovat s ovládacím prvkem.  
  
 Klientské aplikace obvykle nepotřebují pracovat přímo s poskytovateli. Většina standardních ovládacích prvků v aplikacích, které používají rozhraní Win32, model Windows Forms nebo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], je automaticky vystavena [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systému. Aplikace, které implementují vlastní ovládací prvky, mohou také implementovat poskytovatele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pro tyto ovládací prvky a klientské aplikace nemusí provádět žádné zvláštní kroky, aby k nim měli přístup.  
  
 Toto téma poskytuje přehled o tom, jak vývojáři řízení implementují poskytovatele [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zejména pro ovládací prvky v model Windows Forms a v systému Win32.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy zprostředkovatelů  
 Zprostředkovatelé automatizace uživatelského rozhraní spadají do dvou kategorií: poskytovatelé na straně klienta a poskytovatelé na straně serveru.  
  
### <a name="client-side-providers"></a>Poskytovatelé na straně klienta  
 Poskytovatelé na straně klienta jsou implementováni pomocí klientů automatizace uživatelského rozhraní ke komunikaci s aplikací, která nepodporuje, nebo neplně podporuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Poskytovatelé na straně klienta obvykle komunikují se serverem napříč hranicí procesu odesíláním a přijímáním zpráv systému Windows.  
  
 Vzhledem k tomu, že zprostředkovatelé automatizace uživatelského rozhraní pro ovládací prvky v aplikacích Win32, model Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] jsou dodávány jako součást operačního systému, klientské aplikace zřídka musí implementovat své vlastní zprostředkovatele a tento přehled je nepokrývá.  
  
### <a name="server-side-providers"></a>Poskytovatelé na straně serveru  
 Poskytovatelé na straně serveru jsou implementováni vlastními ovládacími prvky nebo aplikacemi, které jsou založeny na jiném uživatelském rozhraní než Win32, model Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Poskytovatelé na straně serveru komunikují s klientskými aplikacemi napříč hranicí procesu vyvoláním rozhraní pro systém [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core, který zase obsluhuje požadavky od klientů.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Koncepce zprostředkovatele automatizace uživatelského rozhraní  
 Tato část poskytuje stručné vysvětlení některých klíčových konceptů, které potřebujete pochopit, aby bylo možné implementovat zprostředkovatele automatizace uživatelského rozhraní.  
  
### <a name="elements"></a>Elementy  
 prvky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou části [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], které jsou viditelné pro klienty automatizace uživatelského rozhraní. Mezi příklady patří okna aplikace, podokna, tlačítka, popisy tlačítek, seznamy a položky seznamu.  
  
### <a name="navigation"></a>Navigace  
 prvky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou zpřístupněny klientům jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sestaví strom tak, že přejdete z jednoho prvku na jiný. Navigace je povolena poskytovateli pro každý prvek, z nichž každá může ukazovat na nadřazenou položku, na stejné úrovni a na podřízené objekty.  
  
 Další informace o zobrazení klienta stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Zobrazení  
 Klient nástroje může zobrazit strom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve třech hlavních zobrazeních, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Nezpracované zobrazení|Obsahuje všechny prvky.|  
|Zobrazení ovládacích prvků|Obsahuje prvky, které jsou ovládacími prvky.|  
|Zobrazení Content (Obsah)|Obsahuje prvky, které mají obsah.|  
  
 Další informace o klientských zobrazeních [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
 Je zodpovědný za implementaci poskytovatele k definování elementu jako obsahu elementu nebo ovládacího prvku. Prvky ovládacího prvku mohou nebo nemusí být zároveň prvky obsahu, ale všechny prvky obsahu jsou ovládací prvky.  
  
### <a name="frameworks"></a>Architektury  
 Rozhraní je komponenta, která spravuje podřízené ovládací prvky, testování přístupů a vykreslování v oblasti obrazovky. Například okno Win32, často označované jako HWND, může sloužit jako rozhraní, které obsahuje více [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvků, jako je například panel nabídek, stavový řádek a tlačítka.  
  
 Ovládací prvky kontejnerů Win32, jako jsou seznamy a stromová zobrazení, se považují za rozhraní, protože obsahují svůj vlastní kód pro vykreslování podřízených položek a pro ně provádí testování na základě volání. Naproti tomu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] seznam není rozhraním, protože vykreslování a testování volání je zpracováváno pomocí okna obsahující [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] v aplikaci lze vytvořit v různých architekturách. Například okno aplikace HWND může obsahovat Dynamic HTML (DHTML), který zase obsahuje komponentu, jako je pole se seznamem v HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Fragment je úplný podstrom prvků z konkrétního rozhraní. Element v kořenovém uzlu podstromu se nazývá kořen fragmentu. Kořen fragmentu nemá nadřazený objekt, ale je hostovaný v jiném rozhraní, obvykle v okně Win32 (HWND).  
  
### <a name="hosts"></a>Hostitelé  
 Kořenový uzel každého fragmentu musí být hostovaný v elementu, obvykle v okně Win32 (HWND). Výjimkou je plocha, která není hostovaná v žádném jiném elementu. Hostitel vlastního ovládacího prvku je HWND samotného ovládacího prvku, nikoli okna aplikace nebo jiné okno, které může obsahovat skupiny ovládacích prvků nejvyšší úrovně.  
  
 Hostitel fragmentu hraje důležitou roli při poskytování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Services. Umožňuje navigaci do kořenového adresáře fragmentů a poskytuje některé výchozí vlastnosti, aby je vlastní zprostředkovatel nemusel implementovat.  
  
## <a name="see-also"></a>Viz také:

- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
