---
title: Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
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
ms.openlocfilehash: ef045ffaac47c6cb196d821c25d96c4d2cd7bf88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254251"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]poskytuje jediné, generalizované rozhraní, které mohou klienti automatizace použít k prošetření nebo provozu uživatelských rozhraní různých platforem a architektur. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]povoluje kód pro zajištění kvality (testování) a aplikace pro usnadnění, jako jsou čtečky obrazovky, k prozkoumávání prvků uživatelského rozhraní a simulaci interakce uživatele s nimi z jiného kódu. Informace o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] různých platformách najdete v tématu věnovaném usnadnění.  
  
 Toto téma popisuje, jak implementovat zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek, který běží v aplikaci WPF. WPF podporuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím stromové struktury automatizačních objektů, které jsou ve stromové struktuře prvků uživatelského rozhraní. Testovací kód a aplikace, které poskytují funkce pro usnadnění přístupu, mohou využívat partnerské objekty automatizace přímo (pro vnitroprocesové kód) nebo prostřednictvím zobecněného rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], které poskytuje.  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Třídy partnerského vztahu služby Automation  
 WPF ovládá ovládací [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prvky prostřednictvím stromu partnerských tříd, které jsou <xref:System.Windows.Automation.Peers.AutomationPeer>odvozeny z. Podle konvence názvy partnerských tříd začínají názvem třídy ovládacího prvku a končí řetězcem "AutomationPeer". Například <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> je rovnocenná třída <xref:System.Windows.Controls.Button> pro třídu ovládacího prvku. Rovnocenné třídy jsou zhruba ekvivalentní [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] typům ovládacích prvků, ale jsou specifické pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prvky. Kód pro automatizaci, který přistupuje k aplikacím [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] WPF prostřednictvím rozhraní, nepoužívá automatizace partnerských uzlů přímo, ale kód Automation ve stejném prostoru procesu může přímo používat partnerské partnery automatizace.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Integrované partnerské třídy pro automatizaci  
 Prvky implementují třídu partnerského vztahu pro automatizaci, pokud přijmou aktivitu rozhraní od uživatele nebo pokud obsahují informace potřebné uživateli aplikací čtečky obrazovky. Ne všechny vizuální prvky WPF mají partnerské vztahy pro automatizaci. Příklady tříd, které implementují partnerské vztahy automatizace <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>jsou, <xref:System.Windows.Controls.Label>a. Příklady tříd, které neimplementují partnerské vztahy automatizace, jsou třídy, které <xref:System.Windows.Controls.Decorator>jsou odvozeny <xref:System.Windows.Controls.Border>z, například a třídy <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid> založené na, například <xref:System.Windows.Controls.Canvas>a.  
  
 Základní <xref:System.Windows.Controls.Control> třída nemá odpovídající třídu typu peer. Pokud potřebujete, aby rovnocenná třída odpovídala vlastnímu ovládacímu prvku, který <xref:System.Windows.Controls.Control>je odvozen z, měli byste odvodit vlastní <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>rovnocennou třídu z.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Požadavky na zabezpečení u odvozených partnerských uzlů  
 Partnerské vztahy automatizace musí běžet v prostředí s částečným vztahem důvěryhodnosti. Kód v sestavení UIAutomationClient není nakonfigurován tak, aby běžel v prostředí s částečným vztahem důvěryhodnosti, a kód partnerského vztahu automatizace by neměl odkazovat na toto sestavení. Místo toho byste měli použít třídy v sestavení UIAutomationTypes. Například byste měli použít <xref:System.Windows.Automation.AutomationElementIdentifiers> třídu ze sestavení UIAutomationTypes, která odpovídá <xref:System.Windows.Automation.AutomationElement> třídě v sestavení UIAutomationClient. Odkaz na UIAutomationTypes sestavení v kódu partnerského vztahu služby Automation je bezpečný.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Rovnocenná navigace  
 Po nalezení partnerského vztahu pro automatizaci může vnitroprocesové kód procházet stromové struktury voláním metody objektu <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> a. <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> Navigace mezi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prvky v rámci ovládacího prvku je podporována implementací <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> metody druhé strany. Systém automatizace uživatelského rozhraní volá tuto metodu, aby vytvořila strom dílčích prvků obsažených v ovládacím prvku. například seznam položek v poli se seznamem. Výchozí <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> Metoda projde vizuální strom elementů a sestaví strom partnerských vztahů automatizace. Vlastní ovládací prvky přepíšou tuto metodu pro vystavení podřízených prvků klientům automatizace a vrácení partnerských uzlů automatizace prvků, které vyjadřují informace nebo umožňují interakci s uživatelem.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Přizpůsobení v odvozeném partnerském uzlu  
 Všechny třídy, které jsou <xref:System.Windows.UIElement> odvozeny z a <xref:System.Windows.ContentElement> obsahují chráněnou virtuální metodu <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF volá <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> k získání partnerského objektu pro automatizaci pro každý ovládací prvek. Kód automatizace může použít partnerský vztah k získání informací o vlastnostech a funkcích ovládacího prvku a k simulaci interaktivního použití. Vlastní ovládací prvek, který podporuje automatizaci <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> , musí přepsat a vrátit instanci třídy, která je odvozena z. <xref:System.Windows.Automation.Peers.AutomationPeer> Například pokud vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.Primitives.ButtonBase> třídy, pak objekt <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> vrácený by měl být odvozen z <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Při implementaci vlastního ovládacího prvku je nutné přepsat "základní" metody ze základní třídy služby Automation peer, která popisuje chování jedinečné a specifické pro váš vlastní ovládací prvek.  
  
### <a name="override-oncreateautomationpeer"></a>Přepsat OnCreateAutomationPeer  
 Přepište <xref:System.Windows.Automation.Peers.AutomationPeer>metodu vlastního ovládacího prvku tak, aby vracel váš objekt poskytovatele, který musí být odvozen přímo nebo nepřímo z. <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>  
  
### <a name="override-getpattern"></a>Přepsat GetPattern  
 Partnerské vztahy pro automatizaci zjednodušují některé implementační aspekty poskytovatelů [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na straně serveru, ale vlastní ovládací prvky automatizace musí stále zpracovávat rozhraní vzoru. Podobně jako poskytovatelé non-WPF, partneři podporují vzory řízení tím, že poskytují implementace rozhraní <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> v oboru názvů, <xref:System.Windows.Automation.Provider.IInvokeProvider>jako je například. Rozhraní vzoru ovládacího prvku lze implementovat samotným partnerským vztahem nebo jiným objektem. Implementace druhé strany <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> vrátí objekt, který podporuje určený vzor. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]kód volá <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metodu a <xref:System.Windows.Automation.Peers.PatternInterface> určí hodnotu výčtu. Vaše přepsání <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> by mělo vracet objekt, který implementuje zadaný vzor. Pokud váš ovládací prvek nemá vlastní implementaci vzoru, můžete volat implementaci <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> základního typu pro načtení buď jeho implementace, nebo hodnotu null, pokud není vzor pro tento typ ovládacího prvku podporován. Například vlastní ovládací prvek NumericUpDown lze nastavit na hodnotu v rámci rozsahu, takže jeho [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] partnerský uzel by <xref:System.Windows.Automation.Provider.IRangeValueProvider> implementoval rozhraní. Následující příklad ukazuje, jak je <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metoda partnerského vztahu přepsána pro reakci <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> na hodnotu.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> Metoda může také určit dílčí prvek jako poskytovatele vzoru. Následující kód ukazuje, jak <xref:System.Windows.Controls.ItemsControl> přesměruje zpracování vzorů posouvaných na <xref:System.Windows.Controls.ScrollViewer> partnerský uzel svého interního řízení.  
  
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
  
 Chcete-li určit dílčí prvek pro zpracování vzorku, tento kód získá objekt podprvku, vytvoří partnerský uzel pomocí <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> metody, <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> nastaví vlastnost nového partnerského vztahu na aktuální partnerský uzel a vrátí nového partnera. Nastavení <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> u dílčího prvku zabraňuje zobrazení dílčího prvku ve stromové struktuře automatizace a určuje všechny události, které dílčí prvek vyvolal jako původ z ovládacího prvku určeného v <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. Ovládací prvek se nezobrazuje ve stromu automatizace a události, které generuje, se zobrazí, aby vznikly <xref:System.Windows.Controls.ItemsControl> z objektu. <xref:System.Windows.Controls.ScrollViewer>  
  
### <a name="override-core-methods"></a>Přepsat metody "Core"  
 Kód pro automatizaci získává informace o ovládacím prvku voláním veřejných metod třídy peer. Chcete-li poskytnout informace o ovládacím prvku, přepište každou metodu, jejíž název končí řetězcem "Core", pokud se vaše implementace ovládacího prvku liší od třídy, která je poskytována základní třídou peere Automation. Minimální, váš ovládací prvek musí implementovat <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> metody a <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> , jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Vaše implementace <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> popisuje svůj ovládací prvek <xref:System.Windows.Automation.ControlType> vrácením hodnoty. I když můžete vrátit <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, měli byste vrátit jeden z konkrétnějších typů ovládacích prvků, pokud přesně popisuje váš ovládací prvek. Návratová hodnota <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> vyžaduje pro implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]poskytovatele dodatečnou práci a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] klientské produkty nemohou odhadnout strukturu ovládacích prvků, interakci s klávesnicí a možné vzory ovládacích prvků.  
  
 Implementujte metody <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>a, abyste označili, jestli váš ovládací prvek obsahuje datový obsah, nebo že v uživatelském rozhraní (nebo v obou) splní interaktivní roli. <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> Ve výchozím nastavení obě metody vrací `true`. Tato nastavení zlepšují použitelnost nástrojů pro automatizaci, jako jsou čtečky obrazovky, které mohou tyto metody použít k filtrování stromu automatizace. Pokud vaše <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metoda přenáší zpracování vzorů na partnerský uzel dílčího prvku, <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> Metoda partnerského uzlu dílčího prvku může vrátit hodnotu false, aby bylo možné skrýt partnerský vztah dílčího prvku ze stromu automatizace. Například <xref:System.Windows.Controls.ListBox> rolování v je zpracováváno <xref:System.Windows.Controls.ScrollViewer>a a partner <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> pro automatizaci pro <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> je vrácen metodou <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> , která je přidružena <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>k. <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> Proto metoda vrátí metodu,takžesevestromuautomatizacenezobrazí.`false` <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>  
  
 Partnerský partner pro automatizaci by měl poskytnout příslušné výchozí hodnoty pro váš ovládací prvek. Všimněte si, že XAML, který odkazuje na váš ovládací prvek, může přepsat vaše partnerské <xref:System.Windows.Automation.AutomationProperties> implementace základních metod zahrnutím atributů. Například následující kód XAML vytvoří tlačítko, které má dvě přizpůsobené [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementace zprostředkovatelů vzorů  
 Rozhraní implementovaná vlastním poskytovatelem jsou explicitně deklarována, pokud vlastnící element je odvozen přímo z <xref:System.Windows.Controls.Control>. Například následující kód deklaruje partnerský vztah pro objekt <xref:System.Windows.Controls.Control> , který implementuje hodnotu rozsahu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Pokud vlastnící ovládací prvek je odvozen z konkrétního typu ovládacího prvku <xref:System.Windows.Controls.Primitives.RangeBase>, jako je například, může být partnerský uzel odvozen od ekvivalentní odvozené třídy typu peer. V tomto případě by byl partnerský uzel odvozen od <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, který poskytuje základní <xref:System.Windows.Automation.Provider.IRangeValueProvider>implementaci. Následující kód ukazuje deklaraci takového partnera.  
  
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
 Klienti automatizace se můžou přihlásit k odběru událostí automatizace. Vlastní ovládací prvky musí nahlásit změny stavu ovládacího prvku voláním <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> metody. Obdobně, když se změní hodnota vlastnosti, zavolejte <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> metodu. Následující kód ukazuje, jak získat partnerský objekt z kódu ovládacího prvku a volat metodu pro vyvolání události. V rámci optimalizace kód určuje, zda pro tento typ události existují nějaké naslouchací procesy. Vyvolání události pouze v případě, že jsou posluchače vyhýbat zbytečné režii a pomáhají ovládacímu prvku udržet reagovat.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled automatizace uživatelského rozhraní](../../ui-automation/ui-automation-overview.md)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../ui-automation/server-side-ui-automation-provider-implementation.md)
- [Vlastní ovládací prvek NumericUpDownC#() na GitHubu](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp)  
- [Vlastní ovládací prvek NumericUpDown (Visual Basic) na GitHubu](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic)
