---
title: Slabý vzor událostí
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f96327f8eaad36f3faebf48db083125816589821
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="weak-event-patterns"></a>Slabý vzor událostí
V aplikacích je možné, že obslužné rutiny, které jsou připojené k zdroje událostí nebude v koordinaci s objektem naslouchací proces, který obslužná rutina připojen ke zdroji. Tato situace může vést k nevracení paměti. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] představuje návrhový vzor, který lze tento problém vyřešit pomocí vyhrazené manager třídu pro konkrétní události a implementace rozhraní na naslouchací procesy pro tuto událost. Tento vzor návrhu se označuje jako *slabé událostí vzor*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Proč implementovat vzor slabé událostí?  
 Naslouchání událostem může vést k nevracení paměti. Typické technika pro naslouchání na událost, je použití syntaxe pro specifický jazyk, který připojí obslužnou rutinu pro událost ve zdroji. Například v jazyce C#, že syntaxe je: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Tento postup vytvoří silné odkaz ze zdroje událostí pro událost naslouchací proces. Obvykle je připojení obslužné rutiny události pro naslouchací proces způsobí, že naslouchací proces má doba života objektu, který je ovlivněno doba života objektu zdroje (Pokud je výslovně odebrali obslužné rutiny události). Ale v některých případech můžete doba života objektu z naslouchacího procesu kontrolován dalších faktorech, například zda aktuálně patří vizuálním stromu aplikace a ne serverem životnost zdroje. Vždy, když doba života objektu zdroj přesahuje doba života objektu naslouchacího procesu, vzoru normálního událostí vede k nevrácenou pamětí: naslouchací proces je udržováno zachování delší než určená.  
  
 Vzor slabé událostí slouží k vyřešení tohoto problému nevracení paměti. Vzor slabé události lze vždy, když potřebuje naslouchací proces registrace pro událost, avšak naslouchací proces nebude vědět explicitně při zrušení registrace. Vzor slabé události mohou sloužit také vždy, když doba života objektu zdroje překračuje doba života užitečné objektu naslouchacího procesu. (V tomto případě *užitečné* je dáno jste.) Vzor slabé událostí umožňuje naslouchací proces se registrovat a přijímat události bez ovlivnění charakteristiky doba života objektu naslouchací proces žádným způsobem. Ve skutečnosti implicitní odkaz ze zdroje není určit, zda naslouchací proces je vhodné pro uvolňování paměti. Odkaz je slabé odkaz, proto pojmenování vzoru slabé události a související [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Naslouchací proces může být paměti shromážděných nebo jinak zničeno a zdroj můžete pokračovat bez zachování noncollectible obslužná rutina odkazy na objekt nyní zničení.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kdo by měla implementovat vzor slabé událostí?  
 Implementace vzoru slabé událostí je zajímavé hlavně pro autory ovládacího prvku. Jako autor ovládací prvek je z velké části zodpovědná chování a členství ve skupině ovládacího prvku a dopad, který má v aplikacích, ve kterých je vložen. To zahrnuje řídit chování doba života objektu, zejména zpracování problému úniku popsané paměti.  
  
 Některé scénáře ze své podstaty samo o vzoru slabé událostí aplikace. Jeden takový scénář se datová vazba. V datové vazby, je běžné zdroje objekt, který má být zcela nezávislé na objekt naslouchací proces, který je cílem vazbu. Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datové vazby již mít vzoru slabé událostí použité v tom, jak jsou implementované události.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Implementace vzoru slabé událostí  
 Existují tři způsoby, jak implementovat vzor slabé událostí. Následující tabulka uvádí se třemi způsoby a nabízí některé pokyny, když každý měli použít.  
  
|Přístup|Kdy implementovat|  
|--------------|-----------------------|  
|Použít existující třídu manager slabé události|Pokud se chcete přihlásit k odběru události má odpovídající <xref:System.Windows.WeakEventManager>, použijte existující správce slabé událostí. Seznam manažerů slabé událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy. Upozorňujeme však, že jsou poměrně málo správci slabé událostí, které jsou součástí WPF, takže budete pravděpodobně muset vyberte jednu z dalších přístupy.|  
|Použití třídy manager obecné slabé událostí|Použít obecný <xref:System.Windows.WeakEventManager%602> pokud stávající <xref:System.Windows.WeakEventManager> má není k dispozici, má snadný způsob, jak implementovat a nemáte zájem o efektivitu. Obecná <xref:System.Windows.WeakEventManager%602> sice méně efektivní než existující nebo vlastní správce slabé událostí. Například obecná třída nepodporuje více reflexe ke zjištění události název události. Navíc kód k registraci události pomocí Obecné <xref:System.Windows.WeakEventManager%602> více podrobné než při použití existující nebo vlastní <xref:System.Windows.WeakEventManager>.|  
|Vytvoření třídy manager vlastní slabé událostí|Vytvoření vlastní <xref:System.Windows.WeakEventManager> pokud stávající <xref:System.Windows.WeakEventManager> není k dispozici, a chcete nejlepšího výkonu. Použití vlastní <xref:System.Windows.WeakEventManager> přihlásit k odběru události bude efektivnější, ale způsobit náklady na zápis další kód na začátku.|  
  
 Následující části popisují, jak implementovat vzor slabé událostí.  Pro účely Tato diskuse se přihlásit k odběru události má následující vlastnosti.  
  
-   Název události je `SomeEvent`.  
  
-   Událost se vyvolá, pomocí `EventSource` třídy.  
  
-   Obslužné rutiny události má typ: `SomeEventEventHandler` (nebo `EventHandler<SomeEventEventArgs>`).  
  
-   Událost předá parametr typu `SomeEventEventArgs` do obslužné rutiny událostí.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Použití existující třídy slabé správce událostí  
  
1.  Najdete existující slabé událost správce.  
  
     Seznam manažerů slabé událostí, které jsou součástí WPF najdete v tématu v hierarchii dědičnosti <xref:System.Windows.WeakEventManager> třídy.  
  
2.  Pomocí nového správce slabé událostí místo normální událostí spojení.  
  
     Pokud například váš kód používá následující vzorec k odběru události:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte jej na vzoru následující:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobně pokud kód používá následující vzor k odhlášení odběru na událost:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Změňte jej na vzoru následující:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Použití obecné třídy slabé správce událostí  
  
1.  Používat obecná <xref:System.Windows.WeakEventManager%602> třída místo normální událostí spojení.  
  
     Při použití <xref:System.Windows.WeakEventManager%602> Chcete-li zaregistrovat naslouchacích procesů událostí, je zadat zdroj události a <xref:System.EventArgs> typů jako parametrů typů třídy a volání <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak je znázorněno v následujícím kódu:  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Vytvoření vlastní třídy slabé správce událostí  
  
1.  Zkopírujte následující šablony třídu do projektu.  
  
     Tato třída dědí z <xref:System.Windows.WeakEventManager> třídy.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  Nahraďte `SomeEventWeakEventManager` název s svůj vlastní název.  
  
3.  Nahraďte tři názvy popsané s odpovídající názvy pro událost. (`SomeEvent`, `EventSource`, a `SomeEventEventArgs`)  
  
4.  Nastavte viditelnost (veřejné / interní / privátní) slabé event – třída manager na stejném viditelnost jako událost, které spravuje.  
  
5.  Pomocí nového správce slabé událostí místo normální událostí spojení.  
  
     Pokud například váš kód používá následující vzorec k odběru události:  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte jej na vzoru následující:  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobně pokud kód používá následující vzor k odhlášení odběru na událost:  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Změňte jej na vzoru následující:  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
