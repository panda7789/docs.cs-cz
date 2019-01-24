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
ms.openlocfilehash: 96107c287003cc5fca2eb0eaa86f0f1f32b7d65e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523694"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>Automatizace uživatelského rozhraní vlastního ovládacího prvku WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] poskytuje jednotné rozhraní zobecněný této služby automation, který můžou klienti použít k prozkoumání a fungovat uživatelských rozhraní z různých platforem a rozhraní. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] Umožňuje (testovací) kontroly kvality kódu a dostupnost aplikace, jako je čtení obrazovky použít k prozkoumání prvky uživatelského rozhraní a simulaci interakce uživatele s nimi z jiného kódu. Informace o [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] na všech platformách, najdete v článku usnadnění přístupu.  
  
 Toto téma popisuje, jak pro implementaci zprostředkovatele automatizace uživatelského rozhraní na straně serveru pro vlastní ovládací prvek, na kterém běží v aplikaci WPF. WPF podporuje [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím stromu objektů automatizace peer parallels stromu prvků uživatelského rozhraní. Testovací kód a aplikace, které poskytují funkce usnadnění můžete použít sdílené objekty automatizace přímo (pro kód v procesu) nebo přes rozhraní zobecněný poskytované [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Sdílené třídy automatizace  
 Řídí podporu WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] prostřednictvím stromu, které jsou odvozeny z třídy peer <xref:System.Windows.Automation.Peers.AutomationPeer>. Podle úmluvy názvy tříd peer začínat název třídy ovládacího prvku a končit "AutomationPeer". Například <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> je třída partnera pro <xref:System.Windows.Controls.Button> třídu ovládacího prvku. Sdílené třídy jsou zhruba odpovídá [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] řídit typy, ale jsou specifické pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy. Automatizace kód, který přistupuje k aplikace WPF pomocí [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] rozhraní nepoužívá automationpeer přímo, ale automationpeer kódu automatizace ve stejném prostoru procesu můžete použít přímo.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Integrované automatizační třídy Peer  
 Prvky implementovat třídu automation peer přijetí rozhraní aktivity uživatele nebo obsahují informace potřebné pro uživatelé čtečky obrazovky aplikace. Ne všechny vizuální prvky WPF mít automationpeer. Příklady tříd, které implementují automationpeer <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, a <xref:System.Windows.Controls.Label>. Příklady tříd, které neimplementují automationpeer jsou třídy, které jsou odvozeny z <xref:System.Windows.Controls.Decorator>, jako například <xref:System.Windows.Controls.Border>a tříd na základě <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.Canvas>.  
  
 Základní <xref:System.Windows.Controls.Control> třída nemá odpovídající třída partnera. Pokud potřebujete sdílené třídy tak, aby odpovídaly vlastní ovládací prvek, který je odvozen od <xref:System.Windows.Controls.Control>, by měla být odvozena třída vlastní sdílené z <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Důležité informace o zabezpečení pro partnerské uzly odvozené  
 Automationpeer musí spustit v prostředí s částečným vztahem důvěryhodnosti. Kód v sestavení UIAutomationClient není konfigurované pro běh v prostředí s částečným vztahem důvěryhodnosti a automation peer kód nesmí odkazovat na toto sestavení. Místo toho byste měli použít třídy v sestavení UIAutomationTypes. Například by měl použít <xref:System.Windows.Automation.AutomationElementIdentifiers> třídy z UIAutomationTypes sestavení, která odpovídá <xref:System.Windows.Automation.AutomationElement> třídy v sestavení UIAutomationClient. Je bezpečné odkazovat na sestavení UIAutomationTypes v automation peer kódu.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Navigace druhé strany  
 Po vyhledání služby automation peer kód v procesu můžete procházet stromu peer voláním objektu <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> metody. Navigace mezi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] druhé strany implementace podporuje prvky v rámci ovládacího prvku <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> metody. Automatizace uživatelského rozhraní systému volá tuto metodu za účelem sestavení stromu podprvky obsažené v rámci ovládacího prvku; například seznam položek v seznamu. Výchozí hodnota <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType> metoda projde vizuální Strom elementů pro sestavení stromu automationpeer. Vlastní ovládací prvky přepsat tuto metodu ke zveřejnění podřízené prvky klientům automatizace, vrací automationpeer prvků, které předání informací nebo Povolit interakci uživatele.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Přizpůsobení v odvozených partnerský uzel  
 Všechny třídy, které jsou odvozeny z <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> obsahovat chráněnou virtuální metodu <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. Volání WPF <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> získat objekt automatizace partnera pro každý ovládací prvek. Automatizace kód může použít partnerským zařízením získat informace o vlastnosti a funkce ovládacího prvku a pro simulaci interaktivních použití. Vlastní ovládací prvek, který podporuje automatizaci musí přepsat <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> a vrátit instanci třídy, která je odvozena z <xref:System.Windows.Automation.Peers.AutomationPeer>. Například, pokud je odvozena z vlastního ovládacího prvku <xref:System.Windows.Controls.Primitives.ButtonBase> třídy a potom objekt vrácený rutinou <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> by měl být odvozen z <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Při implementaci vlastního ovládacího prvku, je nutné přepsat "Základní" metody ze základní klientská automatizační třída partnera, které popisují chování jedinečné a specifické pro vaše vlastní ovládací prvek.  
  
### <a name="override-oncreateautomationpeer"></a>Override OnCreateAutomationPeer  
 Přepsat <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> metodu pro vlastní ovládací prvek tak, že se vrátí objekt zprostředkovatele, který musí být odvozena přímo nebo nepřímo ze <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Přepsat GetPattern  
 Automationpeer Zjednodušte některé aspekty implementace na straně serveru [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] poskytovatelů, ale vlastní ovládací prvek automationpeer stále musí zpracovávat vzor rozhraní. Jako poskytovatelé bez WPF partnerské uzly podpora vzorů ovládacích prvků, jelikož implementuje rozhraní <xref:System.Windows.Automation.Provider?displayProperty=nameWithType> obor názvů, jako například <xref:System.Windows.Automation.Provider.IInvokeProvider>. Rozhraní pro řízení vzor je možné implementovat partnerem sám nebo jiný objekt. Druhé strany provádění <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> vrátí objekt, který podporuje zadanému vzoru. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] kód volá <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metody a určuje <xref:System.Windows.Automation.Peers.PatternInterface> hodnota výčtu. Přepsání metody <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> by měla vrátit objekt, který implementuje zadanému vzoru. Pokud váš ovládací prvek nemá žádné vlastní implementaci vzoru, můžete volat implementaci základní typ <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> načíst jeho implementace nebo hodnota null, pokud vzor není podporovaná pro tento typ ovládacího prvku. Například vlastní ovládací prvek NumericUpDown lze nastavit na hodnotu v rozsahu, takže jeho [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] peer by implementovat <xref:System.Windows.Automation.Provider.IRangeValueProvider> rozhraní. Následující příklad ukazuje jak partnerské <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> reagovat na je přepsána metoda <xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType> hodnotu.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> metodu můžete také určit dílčí prvek jako poskytovatel vzor. Následující kód ukazuje, jak <xref:System.Windows.Controls.ItemsControl> přenosy posuňte vzor zpracování na druhé straně jeho vnitřní <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.  
  
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
  
 K určení dílčího elementu pro vzor zpracování, tento kód načte objekt dílčí element, vytvoří na partnera s použitím <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> metoda, nastaví <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> vlastnosti nového partnerského uzlu na aktuální peer a vrátí nový partnerský uzel. Nastavení <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> na podřízený bránil dílčí element ve stromové struktuře automation peer a označí všechny události vyvolané službou dílčí prvek jako pocházející z ovládacího prvku zadaná v <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. <xref:System.Windows.Controls.ScrollViewer> Ovládací prvek se nezobrazí ve stromu automatizace a posouvání události, které generuje zobrazí jenom na úzkou <xref:System.Windows.Controls.ItemsControl> objektu.  
  
### <a name="override-core-methods"></a>Přepište metody "Základní"  
 Automatizace kód získá informace o váš ovládací prvek voláním veřejné metody třídy peer. Zadání informací o váš ovládací prvek, přepište každou metodu, jejíž název končí řetězcem "Základní" při implementaci ovládacího prvku se liší od, který poskytuje základní klientská automatizační třída partnera. Minimálně musí implementovat ovládacího prvku <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> metod, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Implementace <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> popisuje ovládacího prvku tak, že vrací <xref:System.Windows.Automation.ControlType> hodnotu. Přestože může vrátit <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>, jeden z více konkrétní typy ovládacích prvků by měla vrátit, pokud přesně popisuje ovládacího prvku. Vrácená hodnota <xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType> vyžaduje další práci pro zprostředkovatele pro implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], a [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] klientské produkty nebudou moct předvídat řídicí struktura, interakce klávesnice a vzorů ovládacích prvků je to možné.  
  
 Implementace <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> a <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metod udávající, zda ovládací prvek obsahuje obsah, data nebo splňuje interaktivní role v uživatelském rozhraní (nebo obojí). Ve výchozím nastavení, obě metody vrací `true`. Tato nastavení použitelnosti nástrojů automatizace, jako je čtečky obrazovky, které mohou používat tyto metody pro filtrování stromu automatizace. Pokud vaše <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metoda přenosy vzor zpracování na partnera dílčího elementu, peer dílčího elementu <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metoda může vrátit false, pokud chcete skrýt peer dílčí element ze stromu automatizace. Například posouvání v <xref:System.Windows.Controls.ListBox> zařizuje služba <xref:System.Windows.Controls.ScrollViewer>a partnerskou automatizace pro <xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType> je vrácený <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> metodu <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> , který je přidružený <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Proto <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> metodu <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> vrátí `false`tak, aby <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> se nezobrazí ve stromu automatizace.  
  
 Partnerské služby automation by měla poskytnout vhodnou výchozí hodnoty pro ovládací prvek. Všimněte si, že XAML, který odkazuje na ovládací prvek můžete přepsat váš partner implementace metod core včetně <xref:System.Windows.Automation.AutomationProperties> atributy. Například následující XAML vytvoří tlačítko, které má dva přizpůsobit [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implementace vzoru zprostředkovatelů  
 Rozhraní implementovaná vlastního zprostředkovatele výslovně deklarovány, pokud element vlastnící odvozena přímo z <xref:System.Windows.Controls.Control>. Například následující kód deklaruje pro partnerský uzel <xref:System.Windows.Controls.Control> , který implementuje hodnotu rozsahu.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Pokud je vlastnící ovládací prvek odvozen z určitého typu ovládacího prvku, jako <xref:System.Windows.Controls.Primitives.RangeBase>, partnerský uzel může být odvozena z třídy ekvivalentní odvozené partnera. V takovém případě by odvozovat partnerské <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, který poskytuje základní implementaci <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Následující kód ukazuje deklarace takové partnerský uzel.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Příklad implementace, naleznete v tématu [NumericUpDown vlastní ovládací prvek s ukázka podpora automatizace uživatelského rozhraní a motivu](https://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Vyvolávání událostí  
 Klienti automatizace mohou přihlásit k události automatizace. Vlastní ovládací prvky se musí hlásit změny stav ovládacích prvků pomocí volání <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> metody. Podobně při změně hodnoty vlastnosti, zavolejte <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> metody. Následující kód ukazuje, jak získat objekt sdílené z ovládacího prvku kódu a volání metody k vyvolání události. Optimalizace Určuje kód, pokud jsou všechny moduly pro naslouchání pro tento typ události. Vyvolání události pouze v případě, že existují naslouchacích procesů se vyhnete zbytečnou režii a umožňuje řídit, stále reagovat.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled automatizace uživatelského rozhraní](../../../../docs/framework/ui-automation/ui-automation-overview.md)
- [Ovládací prvek NumericUpDown vlastní motiv a ukázka podpora automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=160025)
- [Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
