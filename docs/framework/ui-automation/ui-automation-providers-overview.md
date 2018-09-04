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
ms.openlocfilehash: 40ad2eb09b4e3a8f78f493311cdb5c0da410943b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560525"
---
# <a name="ui-automation-providers-overview"></a>Přehled zprostředkovatelů automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Zprostředkovatelé automatizace uživatelského rozhraní povolit ovládací prvky pro komunikaci pomocí automatizace uživatelského rozhraní klientských aplikací. Obecné, každý ovládací prvek nebo odlišné elementu v [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] počítaném od zprostředkovatele. Zprostředkovatel zveřejňuje informace o elementu a volitelně implementuje vzorů ovládacích prvků, které umožňují klientské aplikaci pro interakci s ovládacím prvkem.  
  
 Klientské aplikace obvykle nemají pracovat přímo s poskytovatelů. Většina standardních ovládacích prvků v aplikacích používajících [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], nebo [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] architektury jsou automaticky přístupný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] systému. Aplikace, které implementují vlastní ovládací prvky může také implementovat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelů pro tyto ovládací prvky a klientských aplikací není nutné žádné speciální kroky k získání přístupu k nim.  
  
 Toto téma poskytuje přehled implementace ovládacího prvku vývojáři [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelů, zejména pro ovládací prvky v [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] systému windows.  
  
<a name="Types_of_Providers"></a>   
## <a name="types-of-providers"></a>Typy poskytovatelů  
 Zprostředkovatelé automatizace uživatelského rozhraní spadají do dvou kategorií: zprostředkovatele na straně klienta a zprostředkovatele na straně serveru.  
  
### <a name="client-side-providers"></a>Zprostředkovatele na straně klienta  
 Zprostředkovatele na straně klienta jsou implementovány klienty automatizace uživatelského rozhraní pro komunikaci s aplikací, který nepodporuje, nebo plně nepodporuje, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Zprostředkovatele na straně klienta obvykle komunikovat se serverem přes hranice procesu odesílání a příjem zpráv s Windows.  
  
 Protože zprostředkovatelů automatizace uživatelského rozhraní pro ovládací prvky v [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplikace jsou dodávány jako součást operačního systému, klientské aplikace zřídka máte k implementaci vlastních poskytovatelů a tento přehled je nepopisuje Další.  
  
### <a name="server-side-providers"></a>Zprostředkovatele na straně serveru  
 Na straně serveru poskytovatelé se implementují vlastní ovládací prvky nebo aplikacemi, které jsou založeny na architekturu uživatelského rozhraní než [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], Windows Forms nebo [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
 Zprostředkovatele na straně serveru komunikaci s klientskými aplikacemi přes hranice procesu při zavedení rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] základní systém, který zase obsluhuje požadavky od klientů.  
  
<a name="AutomationProviderConcepts"></a>   
## <a name="ui-automation-provider-concepts"></a>Koncepty zprostředkovatele automatizace uživatelského rozhraní  
 Tato část nabízí stručné vysvětlení některých klíčových konceptech, které je potřeba pochopit, aby bylo možné implementace zprostředkovatelů automatizace uživatelského rozhraní.  
  
### <a name="elements"></a>Elementy  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky jsou části [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , které jsou viditelné pro klienty automatizace uživatelského rozhraní. Mezi příklady patří aplikace pro windows, podoken, tlačítek, popisků, pole se seznamem a položky seznamu.  
  
### <a name="navigation"></a>Navigace  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky jsou zveřejněné klientům jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vytvoří tak, že přejdete od jednoho prvku do jiného stromu. Navigace je povolena poskytovatelé pro každý prvek, z nichž každá může odkazovat na nadřazenou položku, na stejné úrovni a podřízené položky.  
  
 Další informace o zobrazení klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
### <a name="views"></a>Zobrazení  
 Klienta můžete zobrazit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury v tři hlavní zobrazení, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Nezpracované zobrazení|Obsahuje všechny prvky.|  
|Ovládací prvek zobrazení|Obsahuje elementy, které jsou ovládací prvky.|  
|Zobrazení obsahu|Obsahuje elementy, které mají obsah.|  
  
 Další informace o zobrazení klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 Je odpovědností implementace poskytovatele definujte element jako content element nebo ovládací prvek. Ovládací prvek může nebo nemusí být také elementů obsahu, ale všechny prvky obsahu jsou ovládací prvky.  
  
### <a name="frameworks"></a>Rozhraní  
 Architektura je komponenta, která spravuje podřízených ovládacích prvků, spuštění testu a vykreslení v oblasti obrazovky. Například [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okna, označovaný také jako HWND, může sloužit jako systém, který obsahuje více [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky jako panel nabídek, stavový řádek a tlačítka.  
  
 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] Určuje kontejner, jako jsou například seznamy a stromové zobrazení jsou považovány za rozhraní, protože obsahují vlastní kód pro vykreslování podřízených položek a provádění spuštění testu na ně. Naopak [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] pole se seznamem není rozhraní .NET framework, protože vykreslování a spuštění testu se zařizuje služba obsahující [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] v aplikaci může být tvořen různá rozhraní. Například může obsahovat okna aplikace HWND [!INCLUDE[TLA#tla_dhtml](../../../includes/tlasharptla-dhtml-md.md)] který zase obsahuje součást, například pole se seznamem v popisovačem HWND.  
  
### <a name="fragments"></a>Fragmenty  
 Je nějaký fragment podstromu prvky z konkrétní rozhraní. Element v kořenovém uzlu podstrom se nazývá kořenového fragment. Fragment kořenové nemá nadřazenou položku, ale je hostována v některých jiných rozhraní .NET framework, obvykle [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] okno (HWND).  
  
### <a name="hosts"></a>Hostitelé  
 Kořenový uzel každé fragmentu musí být hostovaný v elementu, obvykle [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] okno (HWND). Výjimkou je plochy, která není hostována v jiného elementu. Je hostitel vlastního ovládacího prvku HWND samotný ovládací prvek, ne okno aplikace nebo jakékoli okno, které mohou obsahovat skupin ovládacích prvků nejvyšší úrovně.  
  
 Hostitele fragment hraje důležitou roli při poskytování [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služby. Umožňuje navigace na fragment kořen a poskytuje některé výchozí vlastnosti tak, aby vlastního zprostředkovatele pro jejich implementaci.  
  
## <a name="see-also"></a>Viz také  
 [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
