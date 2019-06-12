---
title: Slabý vzor událostí
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 0c5bae64fbbeddedd905e5df0b5789542e29f2f1
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833934"
---
# <a name="weak-event-patterns"></a>Slabý vzor událostí
V aplikacích je možné, že obslužné rutiny, které jsou připojeny ke zdrojům událostí nebude ve spolupráci s objektem naslouchací proces, který připojuje ke zdroji obslužné rutiny. Tato situace může vést k nevracení paměti. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zavádí návrhový vzor, který je možné tento problém vyřešit tak, že třída vyhrazený správce poskytuje pro určité události a implementace rozhraní pro naslouchací procesy pro tuto událost. Tento vzor návrhu se označuje jako *slabý vzor událostí*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Proč implementovat vzor slabých událostí?  
 Naslouchání událostem může vést k nevracení paměti. Typickou techniku pro naslouchání události je syntaxí specifické pro jazyk, který připojí obslužnou rutinu události ve zdroji. Například v C#, že syntaxe je: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Tento postup vytvoří silného odkazu ze zdroje události do event listener. Obvykle připojení obslužnou rutinu události pro naslouchací proces způsobí, že naslouchací proces má dobu života objektu, který ovlivňuje dobu života objektu zdroje (Pokud obslužná rutina události je výslovně odebrali). Ale v některých případech může být vhodné doba života objektu naslouchacího procesu pro řídit pomocí dalších faktorů, jako například, jestli aktuálně patří do vizuálního stromu, aplikace a ne životnost zdroje. Pokaždé, když se doba života objektu zdroje se rozpíná za dobu života objektu naslouchacího procesu, vzor normální událost povede k nevrácení paměti: naslouchací proces je udržována nehledě déle, než bylo zamýšleno.  
  
 Slabý vzor událostí je navržená pro vyřešení tohoto problému nevracení paměti. Pokaždé, když se naslouchací proces potřebuje k registraci na událost, ale naslouchací proces nezná explicitně při zrušení registrace je možné slabý vzor událostí. Slabý vzor událostí je také možné pokaždé, když se doba života objektu zdroje překračuje dobu života objektu užitečné naslouchacího procesu. (V tomto případě *užitečné* se určuje podle vás.) Slabý vzor událostí umožňuje naslouchací proces, zaregistrujte se a přijímat události bez ovlivnění vlastnosti doby života objektu naslouchacího procesu žádným způsobem. V důsledku toho implicitní odkaz ze zdroje nezjišťuje, zda naslouchací proces má nárok na uvolňování paměti. Odkaz je slabý odkaz, tedy pojmenování slabý vzor událostí a související [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Naslouchací proces může být uvolňování paměti shromažďovaným nebo jinak zničeny a zdroji můžete pokračovat bez zachování utvořit obslužná rutina odkazy na nyní zničení objektu.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kdo by měly implementovat vzor slabých událostí?  
 Implementace vzoru slabých událostí je zajímavé hlavně pro autory ovládacího prvku. Jako autor ovládací prvek jsou do značné míry zodpovědná za chování a členství ve skupině ovládacího prvku a dopad, který má u aplikací, ve kterých je vložen. To zahrnuje řízení chování doba života objektu, zejména zpracování problém nevracení paměti popsané.  
  
 Některé scénáře ze své podstaty přizpůsobují aplikace slabý vzor událostí. Jeden takový scénář je datové vazby. V datové vazbě je běžné, že zdrojový objekt nezávislou naslouchací proces objektu, který je cílem vazby. Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby již mít slabý vzor událostí v tom, jak jsou implementované událostí.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Jak implementovat slabý vzor událostí  
 Existují tři způsoby, jak implementovat slabý vzor událostí. Následující tabulka uvádí se třemi způsoby a poskytuje pokyny, kdy by každý používá.  
  
|Přístup|Kdy k implementaci|  
|--------------|-----------------------|  
|Použít existující třídu správce slabých událostí|Pokud se chcete přihlásit k odběru události nemá odpovídající <xref:System.Windows.WeakEventManager>, použijte existujícího správce slabých událostí. Seznam správců slabých událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy. Vzhledem k tomu, že správce součástí slabých událostí jsou omezeny, bude pravděpodobně muset zvolte jednu z dalších přístupů.|  
|Použití třídy obecného slabých událostí správce|Použití obecného <xref:System.Windows.WeakEventManager%602> pokud stávající <xref:System.Windows.WeakEventManager> má není k dispozici, má snadný způsob, jak implementovat a nemáte zájem o efektivitu. Obecné <xref:System.Windows.WeakEventManager%602> je méně efektivní než existující nebo vlastní správce slabých událostí. Například obecná třída nemá další reflexi ke zjišťování událostí, název události. Navíc kód pro registraci na událost pomocí obecného <xref:System.Windows.WeakEventManager%602> podrobné než při použití existující nebo vlastní <xref:System.Windows.WeakEventManager>.|  
|Vytvořte třídu správce vlastní slabých událostí|Vytvoření vlastní <xref:System.Windows.WeakEventManager> pokud stávající <xref:System.Windows.WeakEventManager> není k dispozici a chcete, aby nejlepšího výkonu. Použití vlastní <xref:System.Windows.WeakEventManager> přihlásit k odběru události bude mnohem efektivnější, ale účtovat náklady na vytváření další kódu na začátku.|  
|Pomocí Správce slabých událostí třetích stran|NuGet má [několik správci slabých událostí](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) a také podpora vzor mnoha architektur WPF (například naleznete v tématu [modulu Prism dokumentaci k odběru událostí volně](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).|

 Následující části popisují, jak implementovat vzor slabých událostí.  Pro účely této diskuse Přihlaste se k odběru události má následující vlastnosti.  
  
- Je název události `SomeEvent`.  
  
- Událost je vyvolána `EventSource` třídy.  
  
- Obslužná rutina události má typ: `SomeEventEventHandler` (nebo `EventHandler<SomeEventEventArgs>`).  
  
- Událost předává parametr typu `SomeEventEventArgs` obslužné rutiny události.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Použití existující třídy slabé správce událostí  
  
1. Najděte si událost ve stávající slabé správce.  
  
     Seznam správců slabých událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy.  
  
2. Pomocí nového správce slabých událostí místo normální událost propojení.  
  
     Pokud například váš kód používá následující vzor k odběru události:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte ho na následujícímu vzoru:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobně pokud váš kód používá následující vzor na zrušit odběr události:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte ho na následujícímu vzoru:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Použití obecné třídy slabé správce událostí  
  
1. Použití obecného <xref:System.Windows.WeakEventManager%602> třídy místo normální událost propojení.  
  
     Při použití <xref:System.Windows.WeakEventManager%602> zaregistrovat naslouchacích procesů událostí, zadáte zdroj události a <xref:System.EventArgs> typ jako parametry typu třídy a volání <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak je znázorněno v následujícím kódu:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Vytvoření vlastní třídy slabé správce událostí  
  
1. Zkopírujte následující šablony třídy do projektu.  
  
     Tato třída dědí z <xref:System.Windows.WeakEventManager> třídy.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. Nahradit `SomeEventWeakEventManager` název nahraďte vlastním názvem.  
  
3. Nahraďte tři popsané dříve se odpovídající názvy pro událost. (`SomeEvent`, `EventSource`, a `SomeEventEventArgs`)  
  
4. Nastavte viditelnost (veřejné / interní nebo privátní) třídy správce slabých událostí pro stejnou viditelnost jako událost, kterou spravuje.  
  
5. Pomocí nového správce slabých událostí místo normální událost propojení.  
  
     Pokud například váš kód používá následující vzor k odběru události:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte ho na následujícímu vzoru:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobně pokud váš kód k odhlášení odběru událostí používá následující vzorec:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Změňte ho na následujícímu vzoru:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
