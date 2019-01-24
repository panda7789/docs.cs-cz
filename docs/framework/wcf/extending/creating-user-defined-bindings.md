---
title: Vytváření uživatelem definovaných vazeb
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 6b3a5bbc93fa6465f70295cc6a3d7528039fb787
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548791"
---
# <a name="creating-user-defined-bindings"></a>Vytváření uživatelem definovaných vazeb
Existuje několik způsobů, jak vytvořit vazby není k dispozici v systému:  
  
-   Vytvoření vlastní vazby, na základě <xref:System.ServiceModel.Channels.CustomBinding> třídy, což je kontejner, který vyplnit elementů vazby. Vlastní vazba se pak přidá do koncového bodu služby. Můžete vytvořit vlastní vazby, ať už prostřednictvím kódu programu nebo v konfiguraci application souboru. Chcete-li použít prvek vazby z konfiguračního souboru aplikace, musíte rozšířit element vazby <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Další informace o vlastních vazeb naleznete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md) a <xref:System.ServiceModel.Channels.CustomBinding>.  
  
-   Můžete vytvořit třídu, která je odvozena od standardní vazbu. Například lze odvodit třídu z <xref:System.ServiceModel.WSHttpBinding> a přepsat <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> metodou získat elementy vazby a vložit vlastní prvek vazby nebo vytvoření určitou hodnotu pro zabezpečení.  
  
-   Můžete vytvořit nový <xref:System.ServiceModel.Channels.Binding> typ úplnou kontrolu nad implementace celé vazby.  
  
## <a name="the-order-of-binding-elements"></a>Pořadí elementů vazby  
 Každý prvek vazby představuje krok zpracování při odesílání nebo přijímání zpráv. Za běhu elementy vazby vytvořte kanály a naslouchací procesy potřebné k vývoji odchozí a příchozí zásobníky kanálu.  
  
 Existují tři hlavní typy elementů vazby: Vazba prvky, kódování elementů vazby a elementů vazby přenosu protokolu.  
  
 Prvky vazeb protokolu – Tyhle elementy reprezentují vyšší úrovně kroky zpracování, které mohly reagovat na zprávy. Kanály a naslouchací procesy vytvořené tyto elementy vazby můžete přidat, odebrat nebo změnit obsah zprávy. Zadaná vazba může mít libovolný počet elementů vazby protokolu, každý dědění z <xref:System.ServiceModel.Channels.BindingElement>. Windows Communication Foundation (WCF) obsahuje několik elementů vazby protokolu, včetně <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Kódování Element vazby – tyto prvky představují transformace mezi zprávu a kódování připravené pro přenos na lince. Typické vazby WCF obsahovat přesně jeden element vazby kódování. Příklady kódování elementů vazby <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Pokud kódování element vazby není zadané pro vazbu, bude použito výchozí kódování. Výchozí hodnota je text, pokud je přenos protokolu HTTP a binární jinak.  
  
 Element vazby přenosu – Tyhle elementy reprezentují přenosu kódování zprávy protokolu přenosu. Typické vazby WCF obsahovat právě jeden element vazby přenosu, která dědí z <xref:System.ServiceModel.Channels.TransportBindingElement>. Příklady přenosu elementů vazby <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Při vytváření nové vazby, je důležité pořadí prvků přidaných vazby. Vždy přidáte prvky vazeb v následujícím pořadí:  
  
|Vrstva|Možnosti|Požadováno|  
|-----------|-------------|--------------|  
|Tok transakcí|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Ne|  
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Ne|  
|Kompozitní duplexní režim|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Ne|  
|Kódování|Text, binární soubor, MTOM, vlastní|Ano*|  
|Přenos|TCP, Named Pipes, HTTP, HTTPS, MSMQ, Custom|Ano|  
  
 * Vzhledem k tomu kódování se vyžaduje pro každou vazbu, pokud kódování není zadán, WCF přidá výchozí kódování pro vás. Výchozí hodnota je Text/XML pro přenosy HTTP a HTTPS a binární jinak.  
  
## <a name="creating-a-new-binding-element"></a>Vytvoření nového elementu vazby  
 Kromě typů odvozených z <xref:System.ServiceModel.Channels.BindingElement> , které jsou k dispozici ve WCF, můžete vytvořit vlastní elementy vazby. Díky tomu můžete přizpůsobit tak, jak vytvořit stack vazby a komponenty, které najdete v něm tak, že vytvoříte vlastní <xref:System.ServiceModel.Channels.BindingElement> , který se může skládat s jinými poskytované systémem typy v zásobníku.  
  
 Například, pokud se rozhodnete implementovat `LoggingBindingElement` , která poskytuje schopnost protokolovat zprávy do databáze, je nutné umístit nad přenosový kanál v zásobníku kanálu. V tomto případě aplikace vytvoří vlastní vazby, který se skládá `LoggingBindingElement` s `TcpTransportBindingElement`, jako v následujícím příkladu.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Jak psát váš nový prvek vazby, závisí na jeho přesná funkce. Jednou z ukázek, [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), poskytuje podrobný popis toho, jak implementovat jeden typ elementu vazby.  
  
## <a name="creating-a-new-binding"></a>Vytváří se nová vazba  
 Element vazby uživatel vytvořil lze použít dvěma způsoby. V předchozím oddílu ukazuje první způsob: prostřednictvím vlastní vazby. Vlastní vazba umožňuje uživateli vytvořit své vlastní vazbu na základě libovolného sady elementů, včetně těch uživatel vytvořil vazby.  
  
 Pokud tuto vazbu využíval ve více než jednu aplikaci, vytvořte vlastní vazby a rozšířit <xref:System.ServiceModel.Channels.Binding>. Tím se vyhnete ruční vytvoření vlastní vazby pokaždé, když chcete použít. Uživatelem definované vazby umožňuje definovat chování vazby a obsahují prvky uživatelem definované vazby. A je *předem zabalené*: není nutné znovu vytvořit vazby pokaždé, když ho používáte.  
  
 Minimálně musí implementovat uživatelem definované vazby <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metoda a <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastnost.  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Metoda vrátí nový <xref:System.ServiceModel.Channels.BindingElementCollection> obsahující prvky vazby pro vazbu. Kolekce je seřazen a může obsahovat elementy vazby protokolu nejprve, za nímž následuje kódování element vazby, za nímž následuje element vazby přenosu. Při používání vazeb poskytovaných systémem WCF prvků, je třeba dodržovat element vazby řazení pravidla stanovená dokumentem [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md). Tato kolekce by měly odkazovat nikdy objekty, v rámci třídy uživatelem definované vazby; v důsledku toho musí vracet vazby autoři `Clone()` z <xref:System.ServiceModel.Channels.BindingElementCollection> pro všechna volání <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Vlastnost představuje schéma identifikátoru URI pro přenosový protokol používá ve vazbě. Například *WSHttpBinding* a *NetTcpBinding* vrátit "http" a "net.tcp" z jejich odpovídajících <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastnosti.  
  
 Úplný seznam volitelné metody a vlastnosti pro uživatelem definované vazby, naleznete v tématu <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Příklad  
 Implementuje vazba profilu v tomto příkladu `SampleProfileUdpBinding`, která je odvozena z <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Obsahuje až čtyři elementy vazby v něm: jeden uživatel vytvořil `UdpTransportBindingElement`; a tři poskytované systémem: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, a `ReliableSessionBindingElement`.  
  
```csharp
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
 Ne všechny prvky vazeb jsou navzájem kompatibilní. Konkrétně existují některá omezení týkající se zabezpečení elementů vazby při použití s duplexní kontrakty.  
  
### <a name="one-shot-security"></a>Konečný zabezpečení  
 Můžete implementovat "jednorázové" zabezpečení, všechny potřebné zabezpečené přihlašovací údaje se odešle do jedné zprávy tak, že nastavíte `negotiateServiceCredential` atribut \<zpráva > prvku konfigurace `false`.  
  
 Konečný ověřování nefunguje s duplexní kontrakty.  
  
 Pro kontraktů požadavek-odpověď, jednorázové ověření funguje pouze v případě, že vazba zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instancí.  
  
 Pro jednosměrné kontrakty, jednorázové ověření funguje v případě, že vazba zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> nebo <xref:System.ServiceModel.Channels.IOutputSessionChannel> instancí.  
  
### <a name="cookie-mode-security-context-tokens"></a>Režim souborů cookie tokeny kontextu zabezpečení  
 Tokeny kontextu zabezpečení souborů cookie režimu nelze použít s duplexní kontrakty.  
  
 Pro kontraktů požadavek-odpověď, tokeny kontextu zabezpečení režim souborů cookie pracovní pouze v případě vazby zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instancí.  
  
 Pro jednosměrné kontrakty, kontext zabezpečení režim souborů cookie tokeny funguje, pokud vazba zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instancí.  
  
### <a name="session-mode-security-context-tokens"></a>Režim relace tokeny kontextu zabezpečení  
 Režim relace SCT funguje pro duplexní kontrakty, pokud vazba zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel> nebo <xref:System.ServiceModel.Channels.IDuplexSessionChannel> instancí.  
  
 Režim relace SCT funguje pro požadavek-odpověď smlouvy, pokud vazba zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel>, instance.  
  
 Režim relace SCT funguje pro kontrakty 1-způsob, jak v případě vazby zásobníku pod element vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instancí.  
  
## <a name="deriving-from-a-standard-binding"></a>Odvozený od standardního vazby  
 Místo vytvoření zcela nové třídy vazby, je možné si můžete rozšířit jednu existující vazby poskytované systémem. Podobně jako v předchozím případě je nutné přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metoda a <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.Binding>
- [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
