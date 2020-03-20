---
title: Vytváření uživatelem definovaných vazeb
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 34100569dc5cd5a340abca66fedca40ba21c1e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185635"
---
# <a name="creating-user-defined-bindings"></a>Vytváření uživatelem definovaných vazeb
Existuje několik způsobů, jak vytvořit vazby, které nejsou poskytovány systémem:  
  
- Vytvořte vlastní vazbu <xref:System.ServiceModel.Channels.CustomBinding> na základě třídy, což je kontejner, který vyplníte prvky vazby. Vlastní vazba je pak přidán a koncový bod služby. Vlastní vazbu můžete vytvořit programově nebo v konfiguračním souboru aplikace. Chcete-li použít element vazby z konfiguračního souboru aplikace, musí být prvek vazby rozšířen <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Další informace o vlastní vazby naleznete <xref:System.ServiceModel.Channels.CustomBinding> [v tématu vlastní vazby](custom-bindings.md) a .  
  
- Můžete vytvořit třídu, která je odvozena ze standardní vazby. Můžete například odvodit <xref:System.ServiceModel.WSHttpBinding> třídu <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> z a přepsat metodu získat elementy vazby a vložit vlastní element vazby nebo vytvořit určitou hodnotu pro zabezpečení.  
  
- Můžete vytvořit nový <xref:System.ServiceModel.Channels.Binding> typ zcela řídit celou implementaci vazby.  
  
## <a name="the-order-of-binding-elements"></a>Pořadí vazebných prvků  
 Každý element vazby představuje krok zpracování při odesílání nebo přijímání zpráv. Za běhu prvky vazby vytvořit kanály a naslouchací procesy nezbytné k vytvoření odchozí a příchozí kanál zásobníky.  
  
 Existují tři hlavní typy elementů vazby: Elementy vazby protokolu, Prvky vazby kódování a Prvky vazby přenosu.  
  
 Elementy vazby protokolu – tyto prvky představují vyšší úrovně zpracování kroky, které působí na zprávy. Kanály a naslouchací procesy vytvořené těmito prvky vazby můžete přidat, odebrat nebo upravit obsah zprávy. Daná vazba může mít libovolný počet elementů vazby protokolu, z nichž každý dědí z <xref:System.ServiceModel.Channels.BindingElement>. Windows Communication Foundation (WCF) obsahuje několik <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> prvků <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>vazby protokolu, včetně a .  
  
 Kódování element vazby – tyto prvky představují transformace mezi zprávou a kódování připravené pro přenos na drátě. Typické WCF vazby obsahují přesně jeden prvek vazby kódování. Příklady kódování elementů vazby zahrnují <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Pokud pro vazbu není zadán prvek vazby kódování, použije se výchozí kódování. Výchozí je text, pokud je přenos HTTP a binární jinak.  
  
 Prvek vazby přenosu – tyto prvky představují přenos zprávy kódování na přenosový protokol. Typické WCF vazby zahrnují přesně jeden prvek <xref:System.ServiceModel.Channels.TransportBindingElement>vazby přenosu, který dědí z . Příklady prvků vazby <xref:System.ServiceModel.Channels.TcpTransportBindingElement>přenosu <xref:System.ServiceModel.Channels.HttpTransportBindingElement>zahrnují , <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>, a .  
  
 Při vytváření nových vazeb je důležité pořadí přidaných prvků vazby. Vždy přidejte elementy vazby v následujícím pořadí:  
  
|Vrstva|Možnosti|Požaduje se|  
|-----------|-------------|--------------|  
|Tok transakcí|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Ne|  
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Ne|  
|Složený oboustranný tisk|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Ne|  
|Kódování|Text, Binární, MTOM, Vlastní|Ano\*|  
|Přenos|TCP, pojmenované kanály, HTTP, HTTPS, MSMQ, vlastní|Ano|  
  
\*Vzhledem k tomu, že kódování je vyžadováno pro každou vazbu, pokud není zadáno kódování, WCF přidá výchozí kódování pro vás. Výchozí hodnota je Text/XML pro přenosy HTTP a HTTPS a binární jinak.  
  
## <a name="creating-a-new-binding-element"></a>Vytvoření nového prvku vazby  
 Kromě typů odvozených z, <xref:System.ServiceModel.Channels.BindingElement> které jsou poskytovány WCF, můžete vytvořit vlastní elementy vazby. To umožňuje přizpůsobit způsob vytváření zásobníku vazeb a součásti, které jdou do <xref:System.ServiceModel.Channels.BindingElement> něj vytvořením vlastní, které lze skládat s jinými typy poskytované systémem v zásobníku.  
  
 Například pokud implementujete, `LoggingBindingElement` který poskytuje možnost protokolovat zprávu do databáze, je nutné umístit nad kanál přenosu v zásobníku kanálu. V tomto případě aplikace vytvoří vlastní vazbu, která skládá `LoggingBindingElement` s s `TcpTransportBindingElement`, jako v následujícím příkladu.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),
  new TcpTransportBindingElement()  
);  
```  
  
 Způsob zápisu nového prvku vazby závisí na jeho přesné funkčnosti. Jeden ze vzorků [Transport: UDP](../samples/transport-udp.md), poskytuje podrobný popis, jak implementovat jeden druh prvku vazby.  
  
## <a name="creating-a-new-binding"></a>Vytvoření nové vazby  
 Uživatelem vytvořený element vazby lze použít dvěma způsoby. Předchozí část ilustruje první způsob: prostřednictvím vlastní vazby. Vlastní vazba umožňuje uživateli vytvořit vlastní vazbu na základě libovolné sady elementů vazby, včetně prvků vytvořených uživatelem.  
  
 Pokud použijete vazbu ve více než jedné aplikaci, vytvořte vlastní vazbu a rozšiřte . <xref:System.ServiceModel.Channels.Binding> Tím se zabrání ruční vytvoření vlastní vazby pokaždé, když chcete použít. Uživatelem definovaná vazba umožňuje definovat chování vazby a zahrnout uživatelem definované elementy vazby. A je *předem zabaleno*: není nutné znovu vytvořit vazbu při každém použití.  
  
 Minimálně uživatelem definované vazby musí <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> implementovat <xref:System.ServiceModel.Channels.Binding.Scheme%2A> metodu a vlastnost.  
  
 Metoda <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> vrátí nový, <xref:System.ServiceModel.Channels.BindingElementCollection> který obsahuje elementy vazby pro vazbu. Kolekce je objednána a měla by nejprve obsahovat elementy vazby protokolu, následované elementem vazby kódování, následovaným elementem vazby přenosu. Při použití wcf systémem poskytovány elementy vazby, je nutné dodržovat pravidla řazení elementu vazby zadaná v [custom bindings](custom-bindings.md). Tato kolekce by nikdy odkazovat na objekty odkazované v rámci třídy vazby definované uživatelem; v důsledku toho musí `Clone()` závazní <xref:System.ServiceModel.Channels.BindingElementCollection> autoři vrátit <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>a na každé výzvy .  
  
 Vlastnost <xref:System.ServiceModel.Channels.Binding.Scheme%2A> představuje schéma URI pro přenosový protokol, který se používá ve vazbě. Například *WSHttpBinding* a *NetTcpBinding* vrátí "http" a "net.tcp" z jejich příslušných vlastností. <xref:System.ServiceModel.Channels.Binding.Scheme%2A>  
  
 Úplný seznam volitelných metod a vlastností pro uživatelem definované vazby naleznete v tématu <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Příklad  
 Tento příklad implementuje `SampleProfileUdpBinding`vazbu profilu <xref:System.ServiceModel.Channels.Binding>v , která je odvozena od . Obsahuje `SampleProfileUdpBinding` až čtyři elementy vazby v `UdpTransportBindingElement`něm: jeden user-created ; a tři systémem `TextMessageEncodingBindingElement`poskytované: `CompositeDuplexBindingElement`, `ReliableSessionBindingElement`, a .  
  
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Bezpečnostní omezení s duplexními smlouvami  
 Ne všechny prvky vazby jsou vzájemně kompatibilní. Zejména existují určitá omezení pro prvky vazby zabezpečení při použití s duplexní smlouvy.  
  
### <a name="one-shot-security"></a>Zabezpečení jedním výstřelem  
 Můžete implementovat "one-shot" zabezpečení, kde jsou všechna potřebná pověření zabezpečení `negotiateServiceCredential` odeslána \<v jedné zprávě, nastavením atributu zprávy> konfigurační prvek . `false`  
  
 Jednorázové ověřování nefunguje s duplexními smlouvami.  
  
 U smluv požadavku odpověď jednořízené ověřování funguje pouze v případě, že <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> zásobník vazby pod elementem vazby zabezpečení podporuje vytváření nebo instance.  
  
 U jednosměrných smluv funguje jednočasové ověřování, pokud zásobník vazby <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel>pod <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IOutputSessionChannel> elementem vazby zabezpečení podporuje vytváření , nebo instancí.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokeny kontextu v režimu souborů cookie  
 Tokeny kontextu zabezpečení režimu souborů cookie nelze použít s duplexními smlouvami.  
  
 U smluv požadavek odpověď, tokeny kontextu zabezpečení režimu cookie fungovat pouze <xref:System.ServiceModel.Channels.IRequestChannel> v <xref:System.ServiceModel.Channels.IRequestSessionChannel> případě, že zásobník vazby pod element vazby zabezpečení podporuje vytváření nebo instance.  
  
 Pro jednosměrné smlouvy, tokeny kontextu zabezpečení v režimu souborů cookie funguje, pokud zásobník vazby pod elementem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instance.  
  
### <a name="session-mode-security-context-tokens"></a>Tokeny kontextu v režimu relace  
 Režim relace SCT funguje pro duplexní kontrakty, pokud <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> zásobník vazby pod elementem vazby zabezpečení podporuje vytváření nebo instance.  
  
 Režim relace SCT funguje pro kontrakty Požadavek odpověď, pokud <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>zásobník <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel>vazby pod elementem vazby zabezpečení podporuje vytváření instancí , , nebo .  
  
 Režim relace SCT funguje pro jednosměrné kontrakty, pokud zásobník <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>vazby pod elementem vazby zabezpečení podporuje vytváření , <xref:System.ServiceModel.Channels.IRequestChannel> nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instance.  
  
## <a name="deriving-from-a-standard-binding"></a>Odvození ze standardní vazby  
 Namísto vytvoření zcela nové třídy vazby může být možné rozšířit jednu z existujících vazby poskytované systémem. Stejně jako předchozí případ, je <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> nutné přepsat <xref:System.ServiceModel.Channels.Binding.Scheme%2A> metodu a vlastnost.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.Binding>
- [Vlastní vazby](custom-bindings.md)
