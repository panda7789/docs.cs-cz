---
title: Přehled zprostředkovatelů automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: c8db2e6cbd1f0c0dd61ecb8e147133b8c608ea8f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042045"
---
# <a name="ui-automation-providers-overview"></a>Přehled zprostředkovatelů automatizace uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní umožňují ovládacím prvkům komunikovat s klientskými aplikacemi pro automatizaci uživatelského rozhraní. Obecně [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] je každý ovládací prvek nebo jiný jedinečný prvek v prvku reprezentován poskytovatelem. Zprostředkovatel zpřístupňuje informace o elementu a volitelně implementuje vzory ovládacích prvků, které umožňují klientské aplikaci pracovat s ovládacím prvkem.  
  
 Klientské aplikace obvykle nepotřebují pracovat přímo s poskytovateli. Většina standardních ovládacích prvků v aplikacích, které používají rozhraní [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]nebo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , jsou automaticky zpřístupněna [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systému. Aplikace, které implementují vlastní ovládací prvky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , mohou také implementovat poskytovatele pro tyto ovládací prvky a klientské aplikace nemusí provádět žádné zvláštní kroky, aby k nim měli přístup.  
  
 Toto téma poskytuje přehled o tom, jak vývojáři implementují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatele, zejména pro ovládací prvky v [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] systému a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] Windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy zprostředkovatelů  
 Zprostředkovatelé automatizace uživatelského rozhraní spadají do dvou kategorií: poskytovatelé na straně klienta a poskytovatelé na straně serveru.  
  
### <a name="client-side-providers"></a>Poskytovatelé na straně klienta  
 Poskytovatelé na straně klienta jsou implementováni pomocí klientů automatizace uživatelského rozhraní ke komunikaci s aplikací, která nepodporuje, nebo neplně podporuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Poskytovatelé na straně klienta obvykle komunikují se serverem napříč hranicí procesu odesíláním a přijímáním zpráv systému Windows.  
  
 Vzhledem k tomu, že zprostředkovatelé [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]automatizace uživatelského rozhraní pro [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky v, model Windows Forms nebo aplikace jsou dodávány jako součást operačního systému, klientské aplikace zřídka musí implementovat své vlastní zprostředkovatele a tento přehled je nepokrývá. vyvíjet.  
  
### <a name="server-side-providers"></a>Poskytovatelé na straně serveru  
 Poskytovatelé na straně serveru jsou implementováni vlastními ovládacími prvky nebo aplikacemi, které jsou založeny na jiném [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]uživatelském rozhraní než, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]model Windows Forms nebo.  
  
 Poskytovatelé na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] straně serveru komunikují s klientskými aplikacemi napříč hranicí procesu vyvoláním rozhraní základnímu systému, který zase obsluhuje požadavky klientů.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Koncepce zprostředkovatele automatizace uživatelského rozhraní  
 Tato část poskytuje stručné vysvětlení některých klíčových konceptů, které potřebujete pochopit, aby bylo možné implementovat zprostředkovatele automatizace uživatelského rozhraní.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]prvky jsou části [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , které jsou viditelné pro klienty automatizace uživatelského rozhraní. Mezi příklady patří okna aplikace, podokna, tlačítka, popisy tlačítek, seznamy a položky seznamu.  
  
### <a name="navigation"></a>Navigace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]prvky jsou zpřístupněny klientům jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sestaví strom tak, že přejde z jednoho prvku na jiný. Navigace je povolena poskytovateli pro každý prvek, z nichž každá může ukazovat na nadřazenou položku, na stejné úrovni a na podřízené objekty.  
  
 Další informace o zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
### <a name="views"></a>Zobrazení  
 Klient může zobrazit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom ve třech hlavních zobrazeních, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Nezpracované zobrazení|Obsahuje všechny prvky.|  
|Zobrazení ovládacích prvků|Obsahuje prvky, které jsou ovládacími prvky.|  
|Zobrazení obsahu|Obsahuje prvky, které mají obsah.|  
  
 Další informace o klientských zobrazeních [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
 Je zodpovědný za implementaci poskytovatele k definování elementu jako obsahu elementu nebo ovládacího prvku. Prvky ovládacího prvku mohou nebo nemusí být zároveň prvky obsahu, ale všechny prvky obsahu jsou ovládací prvky.  
  
### <a name="frameworks"></a>Architektury  
 Rozhraní je komponenta, která spravuje podřízené ovládací prvky, testování přístupů a vykreslování v oblasti obrazovky. Například [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okno, často označované jako HWND, může sloužit jako rozhraní, které obsahuje více [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvků, jako je například panel nabídek, stavový řádek a tlačítka.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]ovládací prvky kontejneru, jako jsou seznamy a zobrazení stromové struktury, se považují za rozhraní, protože obsahují svůj vlastní kód pro vykreslování podřízených položek a pro ně provádí testování na základě volání. Naproti tomu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] seznam není rozhraním, protože vykreslování a testování volání je zpracováváno obsahující [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] okno.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] V aplikaci lze vytvořit různé architektury. Například okno aplikace HWND může obsahovat Dynamic HTML (DHTML), který zase obsahuje komponentu, jako je pole se seznamem v HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Fragment je úplný podstrom prvků z konkrétního rozhraní. Element v kořenovém uzlu podstromu se nazývá kořen fragmentu. Kořen fragmentu nemá nadřazený objekt, ale je hostovaný v jiném rozhraní, obvykle v [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] okně (HWND).  
  
### <a name="hosts"></a>Dvou  
 Kořenový uzel každého fragmentu musí být hostovaný v elementu, obvykle [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] v okně (HWND). Výjimkou je plocha, která není hostovaná v žádném jiném elementu. Hostitel vlastního ovládacího prvku je HWND samotného ovládacího prvku, nikoli okna aplikace nebo jiné okno, které může obsahovat skupiny ovládacích prvků nejvyšší úrovně.  
  
 Hostitel fragmentu hraje důležitou roli při poskytování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služeb. Umožňuje navigaci do kořenového adresáře fragmentů a poskytuje některé výchozí vlastnosti, aby je vlastní zprostředkovatel nemusel implementovat.  
  
## <a name="see-also"></a>Viz také:

- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](server-side-ui-automation-provider-implementation.md)
