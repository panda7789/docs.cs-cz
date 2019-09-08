---
title: Vytváření uživatelem definovaných vazeb
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 3b5feb0da86e11485fa7ca1c474a69002c8d43ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797238"
---
# <a name="creating-user-defined-bindings"></a>Vytváření uživatelem definovaných vazeb
Existuje několik způsobů, jak vytvořit vazby, které nejsou poskytovány systémem:  
  
- Vytvořte vlastní vazbu na základě <xref:System.ServiceModel.Channels.CustomBinding> třídy, což je kontejner, který vyplníte prvky vazby. Vlastní vazba je pak přidána do koncového bodu služby. Vlastní vazbu můžete vytvořit buď programově, nebo v konfiguračním souboru aplikace. Chcete-li použít prvek vazby z konfiguračního souboru aplikace, prvek vazby musí být rozšířen <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](custom-bindings.md) and <xref:System.ServiceModel.Channels.CustomBinding>.  
  
- Můžete vytvořit třídu, která je odvozena ze standardní vazby. Například můžete odvodit třídu z <xref:System.ServiceModel.WSHttpBinding> metody a přepsat <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> metodu pro získání prvků vazby a vložení vlastního prvku vazby nebo určení konkrétní hodnoty pro zabezpečení.  
  
- Můžete vytvořit nový <xref:System.ServiceModel.Channels.Binding> typ pro úplné řízení celé implementace vazby.  
  
## <a name="the-order-of-binding-elements"></a>Pořadí prvků vazby  
 Každý prvek vazby představuje krok zpracování při posílání nebo přijímání zpráv. V době běhu vytvoří vazby elementy vytváření kanálů a posluchačů potřebných pro vytváření odchozích a příchozích zásobníků kanálů.  
  
 Existují tři hlavní typy elementů vazby: Prvky vazby protokolu, kódování elementů vazby a elementy vazby přenosu.  
  
 Prvky vazby protokolu – tyto prvky reprezentují kroky zpracování vyšší úrovně, které fungují na zprávách. Kanály a naslouchací procesy vytvořené těmito prvky vazby můžou přidat, odebrat nebo upravit obsah zprávy. Daná vazba může mít libovolný počet elementů vazby protokolu, z <xref:System.ServiceModel.Channels.BindingElement>nichž každá dědí. Windows Communication Foundation (WCF) obsahuje několik elementů vazby protokolu, včetně <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>a.  
  
 Kódování elementu vazby – tyto prvky reprezentují transformace mezi zprávou a kódování připravené pro přenos na lince. Typické vazby WCF obsahují přesně jeden element vazby kódování. Příklady prvků pro kódování vazby zahrnují <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Pokud pro vazbu není zadán element vazby kódování, je použito výchozí kódování. Výchozím nastavením je text v případě, že je přenos HTTP a binární.  
  
 Element vazby přenosu – tyto prvky reprezentují přenos zprávy kódování na transportním protokolu. Typické vazby WCF obsahují přesně jeden element transportních vazeb, který dědí <xref:System.ServiceModel.Channels.TransportBindingElement>z. Příklady elementů vazby přenosu zahrnují <xref:System.ServiceModel.Channels.TcpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Při vytváření nových vazeb je důležité pořadí přidaných prvků vazby. Vždy přidat prvky vazby v následujícím pořadí:  
  
|Vrstva|Možnosti|Požadováno|  
|-----------|-------------|--------------|  
|Tok transakce|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Ne|  
|Spolehlivost|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Ne|  
|Zabezpečení|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Ne|  
|Složený Duplex|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Ne|  
|Kódování|Text, binární, MTOM, vlastní|Ano\*|  
|Přepravu|TCP, pojmenované kanály, HTTP, HTTPS, MSMQ, vlastní|Ano|  
  
\*Vzhledem k tomu, že pro každou vazbu je vyžadováno kódování, pokud není zadáno kódování, WCF přidá pro vás výchozí kódování. Výchozí hodnota je text/XML pro přenosy HTTP a HTTPS a binární soubor v opačném případě.  
  
## <a name="creating-a-new-binding-element"></a>Vytvoření nového elementu vazby  
 Kromě typů odvozených z <xref:System.ServiceModel.Channels.BindingElement> těch poskytovaných službou WCF můžete vytvořit vlastní prvky vazby. To vám umožní přizpůsobit způsob vytvoření zásobníku vazeb a komponenty, které ji najdou, vytvořením vlastní <xref:System.ServiceModel.Channels.BindingElement> , který může být složený z jiných typů poskytovaných systémem v zásobníku.  
  
 Například Pokud implementujete `LoggingBindingElement` , který poskytuje možnost zaprotokolovat zprávu do databáze, musíte ji umístit nad transportní kanál v zásobníku kanálů. V tomto případě aplikace vytvoří vlastní vazbu, která se skládá `LoggingBindingElement` s `TcpTransportBindingElement`, jako v následujícím příkladu.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Způsob psaní nového elementu vazby závisí na jeho přesné funkci. Jedna z ukázek, [přenos: Protokol](../samples/transport-udp.md)UDP poskytuje podrobný popis implementace jednoho druhu elementu vazby.  
  
## <a name="creating-a-new-binding"></a>Vytvoření nové vazby  
 Uživatelsky vytvořený prvek vazby lze použít dvěma způsoby. Předchozí část ilustruje první způsob: prostřednictvím vlastní vazby. Vlastní vazba umožňuje uživateli vytvořit vlastní vazbu založenou na libovolné sadě prvků vazby, včetně uživatelem vytvořených.  
  
 Pokud použijete vazbu ve více než jedné aplikaci, vytvoříte vlastní vazbu a rozšíříte <xref:System.ServiceModel.Channels.Binding>. Tím se vyhnete ručnímu vytváření vlastních vazeb pokaždé, když ji chcete použít. Uživatelsky definovaná vazba umožňuje definovat chování vazby a zahrnout uživatelsky definované prvky vazby. A je *předem zabalená*: nemusíte znovu sestavovat vazbu pokaždé, když ji použijete.  
  
 Alespoň uživatelsky definovaná vazba musí implementovat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodu <xref:System.ServiceModel.Channels.Binding.Scheme%2A> a vlastnost.  
  
 Metoda vrátí nový <xref:System.ServiceModel.Channels.BindingElementCollection> , který obsahuje prvky vazby pro vazbu. <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Kolekce je seřazena a měla by nejprve obsahovat prvky vazby protokolu, za kterými následuje element vazby kódování následovaný elementem vazby přenosu. Při použití elementů vazby poskytovaných systémem, musíte dodržovat pravidla řazení elementů vazby zadaná ve [vlastních vazbách](custom-bindings.md). Tato kolekce nikdy nesmí odkazovat na objekty odkazované v uživatelsky definované třídě vazby; v důsledku toho musí autoři vazby navracet `Clone()` <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>pro každé volání metody. <xref:System.ServiceModel.Channels.BindingElementCollection>  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Vlastnost představuje schéma identifikátoru URI pro transportní protokol používaný pro vazbu. Například *WSHttpBinding* a *NetTcpBinding* vrátí "http" a "NET. TCP" ze svých příslušných <xref:System.ServiceModel.Channels.Binding.Scheme%2A> vlastností.  
  
 Úplný seznam volitelných metod a vlastností pro uživatelsky definované vazby naleznete v tématu <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Příklad  
 Tento příklad implementuje vazbu profilu v `SampleProfileUdpBinding`, která je odvozena <xref:System.ServiceModel.Channels.Binding>z. `TextMessageEncodingBindingElement` `UdpTransportBindingElement` `ReliableSessionBindingElement` `CompositeDuplexBindingElement`Obsahuje až čtyři prvky vazby v rámci něj: jeden uživatelem vytvořený a tři systémy:,, a. `SampleProfileUdpBinding`  
  
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Omezení zabezpečení u duplexních smluv  
 Ne všechny prvky vazby jsou vzájemně kompatibilní. Konkrétně existují určitá omezení pro prvky vazby zabezpečení při použití se duplexní kontrakty.  
  
### <a name="one-shot-security"></a>Zabezpečení jedním Snímekm  
 Můžete implementovat "jednorázové" zabezpečení, kde jsou všechna nezbytná bezpečnostní pověření posílána v jedné zprávě `negotiateServiceCredential` nastavením atributu \<> konfiguračního elementu pro zprávu na `false`.  
  
 Jednorázové ověřování nefunguje u duplexních smluv.  
  
 U kontraktů požadavek-odpověď funguje jednorázové ověřování pouze v případě, že zásobník vazby pod prvkem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> instancí <xref:System.ServiceModel.Channels.IRequestSessionChannel> nebo instancí.  
  
 U jednosměrných smluv funguje jednorázové ověřování, pokud zásobník vazby pod prvkem vazby zabezpečení <xref:System.ServiceModel.Channels.IRequestChannel>podporuje vytváření instancí <xref:System.ServiceModel.Channels.IOutputChannel> , <xref:System.ServiceModel.Channels.IRequestSessionChannel>nebo <xref:System.ServiceModel.Channels.IOutputSessionChannel> .  
  
### <a name="cookie-mode-security-context-tokens"></a>Tokeny kontextu zabezpečení v režimu souborů cookie  
 Tokeny kontextu zabezpečení režimu souborů cookie nelze použít u duplexních kontraktů.  
  
 U kontraktů požadavek-odpověď, tokeny kontextu zabezpečení v režimu souborů cookie fungují pouze v případě, že zásobník vazby pod prvkem <xref:System.ServiceModel.Channels.IRequestChannel> vazby <xref:System.ServiceModel.Channels.IRequestSessionChannel> zabezpečení podporuje vytváření instancí nebo instancí.  
  
 U jednosměrných smluv funguje tokeny kontextu zabezpečení v režimu souborů cookie, pokud zásobník vazeb pod prvkem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IRequestChannel> instancí nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> instancí.  
  
### <a name="session-mode-security-context-tokens"></a>Tokeny kontextu zabezpečení v režimu relace  
 Režim relace SCT funguje pro duplexní kontrakty, pokud zásobník vazby pod prvkem vazby zabezpečení podporuje <xref:System.ServiceModel.Channels.IDuplexChannel> vytváření <xref:System.ServiceModel.Channels.IDuplexSessionChannel> instancí nebo instancí.  
  
 Režim relace SCT funguje pro kontrakty požadavek-odpověď, pokud zásobník vazby pod prvkem vazby zabezpečení podporuje vytváření <xref:System.ServiceModel.Channels.IDuplexChannel>instancí <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> , <xref:System.ServiceModel.Channels.IRequestSessionChannel>nebo.  
  
 Režim relace SCT funguje pro jednosměrné kontrakty, pokud zásobník vazby pod prvkem <xref:System.ServiceModel.Channels.IDuplexChannel>vazby zabezpečení podporuje vytváření instancí <xref:System.ServiceModel.Channels.IRequestChannel> , <xref:System.ServiceModel.Channels.IDuplexSessionChannel>nebo <xref:System.ServiceModel.Channels.IRequestSessionChannel> .  
  
## <a name="deriving-from-a-standard-binding"></a>Odvození ze standardní vazby  
 Místo vytvoření zcela nové třídy vazby je možné, že budete moci zvětšit jednu ze stávajících vazeb poskytovaných systémem. Podobně jako v předchozím případě je nutné přepsat <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> metodu <xref:System.ServiceModel.Channels.Binding.Scheme%2A> a vlastnost.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.Binding>
- [Vlastní vazby](custom-bindings.md)
