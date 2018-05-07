---
title: Vytváření uživatelem definovaných vazeb
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 82fe3baada73b89291311a891069c6ee3f19cf20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-user-defined-bindings"></a>Vytváření uživatelem definovaných vazeb
Chcete-li vytvořit vazby není poskytovaný systému několika způsoby:  
  
-   Vytvoření vlastní vazby, na základě <xref:System.ServiceModel.Channels.CustomBinding> třídy, která je kontejner, který je vyplnit prvky vazeb. Vlastní vazba se pak přidá do koncového bodu služby. Můžete vytvořit vlastní vazby, které buď programově, nebo v konfiguraci aplikace souboru. Pokud chcete použít prvku vazby z konfiguračního souboru aplikace, musíte rozšířit prvku vazby <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Další informace o vlastních vazeb najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md) a <xref:System.ServiceModel.Channels.CustomBinding>.  
  
-   Můžete vytvořit třídu odvozenou od standardní vazby. Například můžete odvození třídy z <xref:System.ServiceModel.WSHttpBinding> a přepsání <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> metoda získat prvky vazby a vložit vlastní vazby element nebo vytvořit konkrétní hodnotu pro zabezpečení.  
  
-   Můžete vytvořit nový <xref:System.ServiceModel.Channels.Binding> typ zcela řídit implementace celý vazby.  
  
## <a name="the-order-of-binding-elements"></a>Pořadí elementů vazby  
 Každý prvek vazby představuje krok zpracování při odesílání nebo přijímání zprávy. V době běhu prvky vazeb vytvořit kanály a naslouchací procesy nezbytné k sestavení odchozí a příchozí zásobníky kanálu.  
  
 Existují tři hlavní typy elementů vazby: prvky vazeb protokolu, kódování prvky vazeb a elementů přenosové vazby.  
  
 Prvky vazeb protokolu – Tyhle elementy reprezentují vyšší úrovně kroky zpracování, které fungují na zprávy. Kanály a naslouchací procesy vytvořené tyto prvky vazeb můžete přidat, odebrat nebo změnit obsah zprávy. Danou vazbu může mít libovolný počet elementů vazby protokolu, každý dědění z <xref:System.ServiceModel.Channels.BindingElement>. Windows Communication Foundation (WCF) obsahuje několik prvky vazby protokolu, včetně <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Kódování prvku vazby – tyto prvky představují transformace mezi zprávu a kódování připraveni k přenosu v drátové síti. Typické [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby obsahovat přesně jeden kódování prvku vazby. Příklady kódování prvky vazeb <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Pokud element kódování vazba není určena pro vazbu, bude použito výchozí kódování. Výchozí hodnota je text při přenosu HTTP a binární jinak.  
  
 Element vazby přenosu – Tyhle elementy reprezentují přenosem kódování zprávy v protokolu přenosu. Typické [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby obsahovat přesně jeden element vazby přenos, který dědí z <xref:System.ServiceModel.Channels.TransportBindingElement>. Příklady přenosu elementů vazby <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Při vytváření nové vazby, je důležité pořadí prvků přidané vazby. Vždy přidáte prvky vazeb v následujícím pořadí:  
  
|Vrstva|Možnosti|Požadováno|  
|-----------|-------------|--------------|  
|Tok transakcí|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Ne|  
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Ne|  
|Složené duplexní režim|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Ne|  
|Kódování|Text, binární, MTOM, vlastní|Ano*|  
|Přenos|TCP, pojmenované kanály, HTTP, HTTPS, služby MSMQ, vlastní|Ano|  
  
 * Protože kódování je vyžadován pro každé vazby, pokud není zadán kódování, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přidá výchozí kódování pro vás. Výchozí hodnota je Text/XML pro přenosy protokolu HTTP a HTTPS a binární jinak.  
  
## <a name="creating-a-new-binding-element"></a>Vytváření nového elementu vazby  
 Kromě typy odvozené z <xref:System.ServiceModel.Channels.BindingElement> , jsou poskytovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], můžete vytvořit vlastní prvky vazeb. To umožňuje přizpůsobit způsob, jakým se vytvoří zásobník vazby a součásti, které v ní přejděte tak, že vytvoříte vlastní <xref:System.ServiceModel.Channels.BindingElement> kterou lze sestavit s další poskytované systémem typy v zásobníku.  
  
 Například, pokud budete implementovat `LoggingBindingElement` , který poskytuje schopnost protokolovat zprávy do databáze, je nutné umístit nad kanál přenosu v zásobníku kanálu. V takovém případě aplikace vytvoří vlastní vazby, která tvoří `LoggingBindingElement` s `TcpTransportBindingElement`, jako v následujícím příkladu.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Jak psát Vaše nového elementu vazby závisí na jeho přesný funkce. Jednou z ukázek, [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), poskytuje podrobný popis toho, jak implementovat jednoho druhu prvku vazby.  
  
## <a name="creating-a-new-binding"></a>Vytvořením vazby  
 Element uživatele vytvořit vazbu lze použít dvěma způsoby. Předchozí část ukazuje první způsob: prostřednictvím vlastní vazby. Vlastní vazby umožňuje uživateli vytvořit své vlastní vazby založené na libovolnou sadu elementů, včetně těch vytvořené uživatelem vazby.  
  
 Pokud používáte vazby ve více než jednu aplikaci, vytvořte vlastní vazbu a rozšířit <xref:System.ServiceModel.Channels.Binding>. Tím je zabráněno ruční vytvoření vlastní vazby pokaždé, když chcete použít. Uživatelem definované vazby umožňuje definovat chování vazby a zahrnují prvky uživatelem definované vazby. A je *předem zabalené*: není nutné znovu vytvořit vazbu pokaždé, když ji používáte.  
  
 Minimálně musí implementovat uživatelem definované vazby <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metoda a <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastnost.  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Metoda vrátí novou <xref:System.ServiceModel.Channels.BindingElementCollection> obsahující prvky vazby pro vazbu. Kolekce je seřadit a by měl obsahovat prvky vazby protokolu nejprve, za nímž následuje kódování prvku vazby, za nímž následuje prvku vazby přenosu. Při použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prvky vazby poskytované systémem, je třeba postupovat podle prvku vazby řazení pravidla stanovená dokumentem [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md). Tato kolekce by měla odkazovat nikdy objekty odkazuje v rámci třídy uživatelem definované vazby; v důsledku toho musí vracet vazby autoři `Clone()` z <xref:System.ServiceModel.Channels.BindingElementCollection> při každém volání <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Vlastnost představuje schéma identifikátoru URI pro přenosový protokol používána na vazby. Například *WSHttpBinding* a *NetTcpBinding* vrácení "http" a "net.tcp" z jejich odpovídajících <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastnosti.  
  
 Úplný seznam volitelné metod a vlastností pro uživatelem definované vazby najdete v tématu <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Příklad  
 Implementuje vazba profilu v tomto příkladu `SampleProfileUdpBinding`, která je odvozena z <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Obsahuje až čtyři prvky vazeb v něm: jeden uživatel vytvořen `UdpTransportBindingElement`; a tři poskytované systémem: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.  
  
```  
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>Omezení zabezpečení s duplexní kontrakty  
 Ne všechny prvky vazby jsou vzájemně kompatibilní. Konkrétně existují některá omezení na zabezpečení prvky vazeb při použití s duplexní kontrakty.  
  
### <a name="one-shot-security"></a>Jednorázové zabezpečení  
 "Jednorázové" zabezpečení, kde jsou všechna potřebná zabezpečovací přihlašovací údaje odeslány do jedné zprávy nastavením můžete implementovat `negotiateServiceCredential` atribut \<zpráva > prvku konfigurace `false`.  
  
 Jednorázové ověřování s duplexní kontrakty nefunguje.  
  
 Pro kontraktů požadavek-odpověď jednorázové ověření funguje pouze v případě, že vazba zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instance.  
  
 Pro jednosměrné kontrakty jednorázové ověření funguje, pokud vazba zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> nebo <xref:System.ServiceModel.Channels.IOutputSessionChannel> instance.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokeny kontextu zabezpečení režim souboru cookie  
 Tokeny kontextu zabezpečení režim souboru cookie nelze použít s duplexní kontrakty.  
  
 Pro kontraktů požadavek-odpověď kontextu zabezpečení režim souboru cookie tokeny pracovní pouze v případě vazby zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instance.  
  
 Kontext zabezpečení režim souboru cookie pro jednosměrné kontrakty tokeny funguje, pokud vazba zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instance.  
  
### <a name="session-mode-security-context-tokens"></a>Režim relace tokenů kontextu zabezpečení  
 Režim relace SCT funguje pro duplexní kontrakty, pokud vazba zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel> nebo <xref:System.ServiceModel.Channels.IDuplexSessionChannel> instance.  
  
 Režim relace SCT funguje pro požadavek-odpověď smlouvy, pokud vazba zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel>, instancí.  
  
 Režim relace SCT funguje pro kontrakty 1 způsob, pokud vazba zásobníku pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instance.  
  
## <a name="deriving-from-a-standard-binding"></a>Odvozování z standardní vazby  
 Místo vytvoření zcela nové třídy vazba, je možné rozšířit jednu z existujících vazby poskytované systémem. Podobně jako v předchozím případě je nutné přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metoda a <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
