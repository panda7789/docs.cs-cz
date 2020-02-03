---
title: Automatizace uživatelského rozhraní vlastního ovládacího prvku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: a370ed2c6b1f3273eca93b4865a032e8299f1cfb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738198"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] poskytuje jediné zobecněné rozhraní, které mohou klienti automatizace použít k prošetření nebo provozu uživatelských rozhraní různých platforem a architektur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] umožňuje posuzovat prvky uživatelského rozhraní a simulovat interakci s uživateli z jiného kódu, jako jsou například čtečky obrazovky. Informace o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] napříč všemi platformami najdete v tématu přístupnost.  
  
 Toto téma popisuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek, který běží v aplikaci WPF. WPF podporuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím stromu automatizačních objektů, které jsou ve stromové struktuře prvků uživatelského rozhraní. Testovací kód a aplikace, které poskytují funkce pro usnadnění přístupu, mohou využívat partnerské objekty automatizace přímo (pro vnitroprocesové kód) nebo prostřednictvím zobecněného rozhraní, které poskytuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Třídy partnerského vztahu služby Automation  
 Ovládací prvky WPF podporují [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím stromu partnerských tříd, které jsou odvozeny z <xref:System.Windows.Automation.Peers.AutomationPeer>. Podle konvence názvy partnerských tříd začínají názvem třídy ovládacího prvku a končí řetězcem "AutomationPeer". <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> je například rovnocenná třída pro třídu ovládacího prvku <xref:System.Windows.Controls.Button>. Rovnocenné třídy jsou zhruba ekvivalentní [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] typů ovládacích prvků, ale jsou specifické pro prvky WPF. Kód pro automatizaci, který přistupuje k aplikacím WPF prostřednictvím rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], nepoužívá přímo partnerské vztahy automatizace, ale kód automatizace ve stejném prostoru procesu může přímo používat partnerské vztahy automatizace.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Integrované partnerské třídy pro automatizaci  
 Prvky implementují třídu partnerského vztahu pro automatizaci, pokud přijmou aktivitu rozhraní od uživatele nebo pokud obsahují informace potřebné uživateli aplikací čtečky obrazovky. Ne všechny vizuální prvky WPF mají partnerské vztahy pro automatizaci. Příklady tříd, které implementují partnerské vztahy automatizace, jsou <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>a <xref:System.Windows.Controls.Label>. Příklady tříd, které neimplementují partnerské vztahy automatizace, jsou třídy, které jsou odvozeny od <xref:System.Windows.Controls.Decorator>, jako je například <xref:System.Windows.Controls.Border>a třídy založené na <xref:System.Windows.Controls.Panel>, jako je například <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.Canvas>.  
  
 Třída Base <xref:System.Windows.Controls.Control> nemá odpovídající třídu typu peer. Pokud potřebujete, aby rovnocenná třída odpovídala vlastnímu ovládacímu prvku, který je odvozen od <xref:System.Windows.Controls.Control>, měli byste odvodit vlastní rovnocennou třídu z <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Požadavky na zabezpečení u odvozených partnerských uzlů  
 Partnerské vztahy automatizace musí běžet v prostředí s částečným vztahem důvěryhodnosti. Kód v sestavení UIAutomationClient není nakonfigurován tak, aby běžel v prostředí s částečným vztahem důvěryhodnosti, a kód partnerského vztahu automatizace by neměl odkazovat na toto sestavení. Místo toho byste měli použít třídy v sestavení UIAutomationTypes. Například byste měli použít třídu <xref:System.Windows.Automation.AutomationElementIdentifiers> ze sestavení UIAutomationTypes, které odpovídá třídě <xref:System.Windows.Automation.AutomationElement> v sestavení UIAutomationClient. Odkaz na UIAutomationTypes sestavení v kódu partnerského vztahu služby Automation je bezpečný.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Rovnocenná navigace  
 Po nalezení partnerského vztahu pro automatizaci může vnitroprocesové kód procházet stromové struktury voláním <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> metody objektu. Navigace mezi prvky WPF v rámci ovládacího prvku je podporována implementací metody <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> druhé strany. Systém automatizace uživatelského rozhraní volá tuto metodu, aby vytvořila strom dílčích prvků obsažených v ovládacím prvku. například seznam položek v poli se seznamem. Výchozí metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> projde vizuální strom elementů a sestaví strom partnerských vztahů automatizace. Vlastní ovládací prvky přepíšou tuto metodu pro vystavení podřízených prvků klientům automatizace a vrácení partnerských uzlů automatizace prvků, které vyjadřují informace nebo umožňují interakci s uživatelem.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Přizpůsobení v odvozeném partnerském uzlu  
 Všechny třídy, které jsou odvozeny od <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> obsahují chráněnou virtuální metodu <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF volá <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> k získání partnerského objektu pro automatizaci pro každý ovládací prvek. Kód automatizace může použít partnerský vztah k získání informací o vlastnostech a funkcích ovládacího prvku a k simulaci interaktivního použití. Vlastní ovládací prvek, který podporuje automatizaci, musí přepsat <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> a vrátit instanci třídy, která je odvozena z <xref:System.Windows.Automation.Peers.AutomationPeer>. Například pokud vlastní ovládací prvek je odvozen z třídy <xref:System.Windows.Controls.Primitives.ButtonBase>, objekt vrácený <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> by měl odvozovat z <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Při implementaci vlastního ovládacího prvku je nutné přepsat "základní" metody ze základní třídy služby Automation peer, která popisuje chování jedinečné a specifické pro váš vlastní ovládací prvek.  
  
### <a name="override-oncreateautomationpeer"></a>Přepsat OnCreateAutomationPeer  
 Přepište metodu <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> vlastního ovládacího prvku tak, aby vrátila objekt poskytovatele, který musí být odvozen přímo nebo nepřímo z <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Přepsat GetPattern  
 Partnerské vztahy pro automatizaci zjednodušují některé implementační aspekty poskytovatelů [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na straně serveru, ale vlastní ovládací prvky automatizace musí nadále zpracovávat rozhraní vzoru. Podobně jako poskytovatelé non-WPF, partneři podporují vzory řízení tím, že poskytují implementace rozhraní v oboru názvů <xref:System.Windows.Automation.Provider?displayProperty=nameWithType>, jako je například <xref:System.Windows.Automation.Provider.IInvokeProvider>. Rozhraní vzoru ovládacího prvku lze implementovat samotným partnerským vztahem nebo jiným objektem. Implementace <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> druhé strany vrátí objekt, který podporuje určený vzor. kód [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] volá metodu <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> a určuje <xref:System.Windows.Automation.Peers.PatternInterface> hodnotu výčtu. Vaše přepsání <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> by mělo vracet objekt, který implementuje zadaný vzor. Pokud váš ovládací prvek nemá vlastní implementaci modelu, můžete volat implementaci <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> základního typu pro načtení buď jeho implementace, nebo hodnotu null, pokud není vzor pro tento typ ovládacího prvku podporován. Například vlastní ovládací prvek NumericUpDown lze nastavit na hodnotu v rozsahu, takže jeho [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] partnerský uzel by implementoval rozhraní <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Následující příklad ukazuje, jak je přepsána metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> partnera, aby reagovala na hodnotu <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 Metoda <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> může také určit dílčí prvek jako poskytovatele vzoru. Následující kód ukazuje, jak <xref:System.Windows.Controls.ItemsControl> přenáší zpracování posouvaných vzorků na partnerský uzel svého interního <xref:System.Windows.Controls.ScrollViewer>ho ovládacího prvku.  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Chcete-li určit dílčí prvek pro zpracování vzorku, tento kód získá objekt podprvku, vytvoří partnerský uzel pomocí metody <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>, nastaví vlastnost <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> nového partnerského vztahu na aktuální partnerský uzel a vrátí nového partnera. Nastavení <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> u dílčího prvku brání zobrazení dílčího prvku ve stromové struktuře automatizace a označuje všechny události, které dílčí prvek vyvolal jako původ z ovládacího prvku určeného v <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> ovládací prvek se nezobrazí ve stromu automatizace a události posouvání, které generuje, se zobrazí, aby vznikly z objektu <xref:System.Windows.Controls.ItemsControl>.  
  
### <a name="override-core-methods"></a>Přepsat metody "Core"  
 Kód pro automatizaci získává informace o ovládacím prvku voláním veřejných metod třídy peer. Chcete-li poskytnout informace o ovládacím prvku, přepište každou metodu, jejíž název končí řetězcem "Core", pokud se vaše implementace ovládacího prvku liší od třídy, která je poskytována základní třídou peere Automation. Přinejmenším musí váš ovládací prvek implementovat metody <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Vaše implementace <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> popisuje svůj ovládací prvek vrácením <xref:System.Windows.Automation.ControlType> hodnoty. I když můžete vrátit <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, měli byste vrátit jeden z konkrétnějších typů ovládacích prvků, pokud přesně popisuje váš ovládací prvek. Návratová hodnota <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> vyžaduje další práci, kterou poskytovatel implementuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] klientských produktech nemůže předvídat strukturu ovládacího prvku, interakci s klávesnicí a možné vzory ovládacích prvků.  
  
 Implementujte metody <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>, abyste označili, jestli váš ovládací prvek obsahuje datový obsah, nebo plnit interaktivní roli v uživatelském rozhraní (nebo v obou). Ve výchozím nastavení obě metody vrací `true`. Tato nastavení zlepšují použitelnost nástrojů pro automatizaci, jako jsou čtečky obrazovky, které mohou tyto metody použít k filtrování stromu automatizace. Pokud vaše metoda <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> přenáší zpracování vzorů na partnerský uzel dílčího prvku, může metoda <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> partnerského uzlu dílčího prvku vracet hodnotu false, aby se z stromu automatizace skryla dílčí uzel. Například posouvání v <xref:System.Windows.Controls.ListBox> je zpracováváno <xref:System.Windows.Controls.ScrollViewer>a partnerská strana pro <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> je vrácena metodou <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>, která je přidružena k <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Proto metoda <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> vrací `false`, takže <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> se nezobrazuje ve stromu automatizace.  
  
 Partnerský partner pro automatizaci by měl poskytnout příslušné výchozí hodnoty pro váš ovládací prvek. Všimněte si, že XAML, který odkazuje na váš ovládací prvek, může přepsat vaše partnerské implementace základních metod zahrnutím atributů <xref:System.Windows.Automation.AutomationProperties>. Například následující kód XAML vytvoří tlačítko, které má dvě přizpůsobené vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementace zprostředkovatelů vzorů  
 Rozhraní implementovaná vlastním poskytovatelem jsou explicitně deklarována, pokud vlastnící prvek je odvozen přímo z <xref:System.Windows.Controls.Control>. Například následující kód deklaruje partnerský vztah pro <xref:System.Windows.Controls.Control>, který implementuje hodnotu rozsahu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Pokud vlastnící ovládací prvek je odvozen z konkrétního typu ovládacího prvku, jako je například <xref:System.Windows.Controls.Primitives.RangeBase>, může být partnerský uzel odvozen od ekvivalentní odvozené třídy typu peer. V takovém případě by se partner mohl odvozovat z <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, která poskytuje základní implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Následující kód ukazuje deklaraci takového partnera.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
Příklad implementace naleznete v tématu zdrojový kód [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) nebo [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) , který implementuje a spotřebovává vlastní ovládací prvek NumericUpDown.  
  
### <a name="raise-events"></a>Vyvolat události  
 Klienti automatizace se můžou přihlásit k odběru událostí automatizace. Vlastní ovládací prvky musí nahlásit změny stavu ovládacího prvku voláním metody <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>. Podobně když se změní hodnota vlastnosti, zavolejte metodu <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>. Následující kód ukazuje, jak získat partnerský objekt z kódu ovládacího prvku a volat metodu pro vyvolání události. V rámci optimalizace kód určuje, zda pro tento typ události existují nějaké naslouchací procesy. Vyvolání události pouze v případě, že jsou posluchače vyhýbat zbytečné režii a pomáhají ovládacímu prvku udržet reagovat.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Viz také

- [Přehled automatizace uživatelského rozhraní](../../ui-automation/ui-automation-overview.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Vlastní ovládací prvek NumericUpDownC#() na GitHubu](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Vlastní ovládací prvek NumericUpDown (Visual Basic) na GitHubu](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
