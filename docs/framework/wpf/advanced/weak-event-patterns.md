---
title: Slabý vzor událostí
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 9f61a5a60b2ba1305158d1ab570079fe6aac19ac
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870737"
---
# <a name="weak-event-patterns"></a>Slabý vzor událostí
V aplikacích je možné, že obslužné rutiny, které jsou připojeny ke zdrojům událostí, nebudou zničeny v koordinaci s objektem naslouchacího procesu, který připojil obslužnou rutinu ke zdroji. Tato situace může vést k nevracení paměti. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zavádí vzor návrhu, který lze použít k vyřešení tohoto problému, poskytnutím vyhrazené třídy správce pro konkrétní události a implementací rozhraní na naslouchací proces pro danou událost. Tento vzor návrhu je známý jako *slabý vzorek události*.  
  
## <a name="why-implement-the-weak-event-pattern"></a>Proč implementovat slabý vzorek události?  
 Poslouchání událostí může vést k nevracení paměti. Typická technika pro naslouchání události je použít syntaxi specifickou pro jazyk, která připojí obslužnou rutinu k události ve zdroji. Například v C#nástroji je tato syntaxe: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.  
  
 Tato technika vytvoří silný odkaz ze zdroje události na naslouchací proces událostí. Obvykle připojení obslužné rutiny události pro naslouchací proces způsobí, že naslouchací proces bude mít životnost objektu, která je ovlivněna životností objektu zdroje (Pokud není obslužná rutina události explicitně odebrána). V některých případech však můžete chtít, aby životnost objektu naslouchacího procesu byla kontrolována jinými faktory, například zda aktuálně patří do vizuálního stromu aplikace, a nikoli po dobu života zdroje. Pokaždé, když životnost zdrojového objektu přesáhne dobu životnosti objektu naslouchacího procesu, vzorek normální události vede k nevrácení paměti: naslouchací proces je udržován v provozu déle, než je určeno.  
  
 Slabý vzorek události je navržen pro vyřešení problému při nevracení paměti. Slabý vzorek události lze použít vždy, když se naslouchací proces potřebuje zaregistrovat pro událost, ale naslouchací proces výslovně neví, kdy zrušit registraci. Slabý vzorek události lze také použít vždy, když životnost objektu zdroje překračuje užitečnou životnost objektu naslouchacího procesu. (V takovém případě je to *užitečné* , je určeno vámi.) Slabý vzorek události umožňuje naslouchací proces registrovat a přijímat události, aniž by to ovlivnilo vlastnosti životnosti objektu naslouchacího procesu. V podstatě implicitní odkaz ze zdroje neurčuje, zda má naslouchací proces nárok na uvolňování paměti. Odkaz je slabý odkaz, takže pojmenováváme slabý vzorek události a související rozhraní API. Naslouchací proces může být shromážděn z paměti nebo jinak zničen a zdroj může pokračovat bez uchování odkazů obslužných rutin utvořit na objekt, který je nyní zničen.  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>Kdo má implementovat slabý vzorek události?  
 Implementace slabého vzoru události je zajímavá hlavně pro autory ovládacích prvků. Jako autor ovládacího prvku je převážně zodpovědný za chování a omezení vašeho řízení a vliv na aplikace, do kterých je vložen. To zahrnuje chování při životnosti řídicích objektů, zejména zpracování popsaného problému při nevracení paměti.  
  
 Některé scénáře jsou z vlastního podstaty zapůjčení do aplikace slabého vzoru události. Jedním z takových scénářů je vázání dat. V datové vazbě je běžné, že zdrojový objekt je zcela nezávislý na objektu naslouchacího procesu, který je cílem vazby. Mnoho aspektů [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] datových vazeb už má slabý vzor událostí, který se používá při implementaci událostí.  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>Jak implementovat slabý vzorek události  
 Existují tři způsoby, jak implementovat slabý vzorek události. Následující tabulka uvádí tři přístupy a poskytuje pokyny pro použití každého z nich.  
  
|Přístup|Kdy implementovat|  
|--------------|-----------------------|  
|Použít stávající slabší třídu správce událostí|Pokud má událost, k jejímuž odběru se chcete přihlásit, odpovídající <xref:System.Windows.WeakEventManager>, použijte stávající správce slabé události. Seznam slabých správců událostí, které jsou součástí WPF, naleznete v hierarchii dědičnosti ve třídě <xref:System.Windows.WeakEventManager>. Vzhledem k tomu, že jsou zahrnuté slabé správce událostí omezené, budete pravděpodobně muset zvolit jeden z dalších přístupů.|  
|Použití obecné třídy slabého správce událostí|Použijte obecné <xref:System.Windows.WeakEventManager%602>, když existující <xref:System.Windows.WeakEventManager> není k dispozici, chcete snadno implementovat a nemáte obavy o efektivitu. Obecné <xref:System.Windows.WeakEventManager%602> je méně efektivní než stávající nebo vlastní slabý správce událostí. Například obecná třída má větší odraz pro zjištění události s ohledem na název události. Také kód pro registraci události pomocí obecného <xref:System.Windows.WeakEventManager%602> je podrobnější než použití existujícího nebo vlastního <xref:System.Windows.WeakEventManager>.|  
|Vytvoření vlastní slabé třídy správce událostí|Pokud není k dispozici existující <xref:System.Windows.WeakEventManager> a chcete nejlepší efektivitu, vytvořte vlastní <xref:System.Windows.WeakEventManager>. Použití vlastního <xref:System.Windows.WeakEventManager> k přihlášení k odběru události bude efektivnější, ale získáte náklady na zápis více kódů na začátku.|  
|Použití slabého správce událostí třetí strany|NuGet má [několik slabých správců událostí](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) a řada platforem WPF také podporuje vzor (například [dokumentaci Prism o volně vázaných odběrech událostí](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).|

 Následující části popisují, jak implementovat slabý vzorek události.  Pro účely této diskuze má událost pro přihlášení k odběru následující charakteristiky.  
  
- Název události je `SomeEvent`.  
  
- Událost je vyvolána třídou `EventSource`.  
  
- Obslužná rutina události je typu: `SomeEventEventHandler` (nebo `EventHandler<SomeEventEventArgs>`).  
  
- Událost předá do obslužných rutin událostí parametr typu `SomeEventEventArgs`.  
  
### <a name="using-an-existing-weak-event-manager-class"></a>Použití stávající slabé třídy správce událostí  
  
1. Najděte stávajícího slabého správce událostí.  
  
     Seznam slabých správců událostí, které jsou součástí WPF, naleznete v hierarchii dědičnosti ve třídě <xref:System.Windows.WeakEventManager>.  
  
2. Místo běžné události propojení použijte nový slabý správce událostí.  
  
     Například pokud váš kód používá následující vzor pro přihlášení k odběru události:  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte ji na následující vzor:  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobně, pokud váš kód používá následující vzor k odhlášení odběru události:  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte ji na následující vzor:  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>Použití obecné třídy slabého správce událostí  
  
1. Místo běžné události propojení použijte obecnou třídu <xref:System.Windows.WeakEventManager%602>.  
  
     Při použití <xref:System.Windows.WeakEventManager%602> k registraci posluchačů událostí, zadejte zdroj události a typ <xref:System.EventArgs> jako parametry typu do třídy a zavolejte <xref:System.Windows.WeakEventManager%602.AddHandler%2A>, jak je znázorněno v následujícím kódu:  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>Vytvoření vlastní slabé třídy správce událostí  
  
1. Zkopírujte následující šablonu třídy do projektu.  
  
     Tato třída dědí z třídy <xref:System.Windows.WeakEventManager>.  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. Název `SomeEventWeakEventManager` nahraďte vlastním názvem.  
  
3. Nahraďte tři výše popsané názvy odpovídajícími názvy pro vaši událost. (`SomeEvent`, `EventSource`a `SomeEventEventArgs`)  
  
4. Nastavte viditelnost (veřejná/interní/privátní) třídy slabého správce událostí na stejnou viditelnost jako událost, kterou spravuje.  
  
5. Místo běžné události propojení použijte nový slabý správce událostí.  
  
     Například pokud váš kód používá následující vzor pro přihlášení k odběru události:  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     Změňte ji na následující vzor:  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     Podobně, pokud váš kód používá následující vzor k odhlášení odběru události:  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     Změňte ji na následující vzor:  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
