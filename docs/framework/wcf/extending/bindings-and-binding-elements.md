---
title: Vazby a prvky vazeb
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: 33ebb07e350dbbbdd324b442f52dfb6287322bd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858374"
---
# <a name="bindings-and-binding-elements"></a>Vazby a prvky vazeb
Vazby jsou kolekce elementů speciální konfigurace, volá *elementů vazby*, které jsou vyhodnocovány pomocí modulu runtime služby vždy, když klient nebo se vytváří koncový bod služby. Typ a pořadí elementů vazby v rámci vazbu určuje výběr a pořadí těchto kanálů protokol a přenosu v zásobníku koncového bodu kanálu.  
  
 Vazby, zejména vazeb poskytovaných systémem, obvykle také mít počet vlastnosti konfigurace, které odpovídají nejčastěji upravené vlastnosti prvky zapouzdřený vazby.  
  
 Vazby musí obsahovat přesně jeden element vazby přenosu. Každý element vazby přenosu znamená výchozí zprávu kódování element vazby, které můžete přepsat tak, že přidáte maximálně jeden element vazby do vazby kódování zprávy. Kromě přenosu a prvky vazeb kodér vazbu může obsahovat libovolný počet elementů vazby protokolu, které společně implementují funkce potřebné pro služby a odešlete zprávu protokolu SOAP z jeden koncový bod. Podrobnosti najdete v tématu [pomocí vazby na konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Rozšiřování vazeb a elementů vazby  
 Windows Communication Foundation (WCF) zahrnuje vazeb poskytovaných systémem, které pokrývají širokou škálu scénářů. (Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).) Může nastat situace, ale pokud potřebujete k vytváření a používání vazbu, která není součástí WCF. Následující scénáře vyžadují vytvoření novou vazbu.  
  
- Pokud chcete použít nový element vazby (například nový přenos, kódování nebo element vazby protokolu), musíte vytvořit novou vazbu, která obsahuje tento element vazby. Například, pokud jste přidali vlastní `UdpTransportBindingElement` pro přenos UDP, je třeba vytvořit novou vazbu, aby využívání. Informace o chování pomocí provádí <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> zadejte naleznete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
- Ke konfiguraci existující elementů vazby způsobem, který vazeb poskytovaných systémem není vystavit na veřejné vlastnosti. Například musíte vytvořit novou vazbu, chcete-li změnit pořadí, ve které podepisování a šifrování jsou operace prováděny. Informace o provádění toto chování najdete v tématu [jak: Přizpůsobení vazeb poskytovaných systémem](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
- K navázání podnikové standardní vazby, která zpřístupňují jenom konkrétní konfiguraci možností. Například chcete vytvořit pro vaši společnost varianta velikostí <xref:System.ServiceModel.WSHttpBinding> vaší společnosti, ve kterém nejde vypnout zabezpečení, vytvořte novou vazbu, který se chová jako <xref:System.ServiceModel.WSHttpBinding>, ale vždy na zabezpečení. Podrobnosti najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
- Obvykle provádět určité přizpůsobení metadat, ale nemusí nutně jít ke konfiguraci nebo použít některé vlastní prvek vazby. Další informace o poskytování podpory metadat vazby a prvky vazeb naleznete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Kanály, vazby a prvky vazeb  
 Vazby a prvky vazeb jsou propojení mezi programovací model pro aplikace, který obsahuje atributy a chování, a model kanálu, který obsahuje objekty pro vytváření a naslouchacích procesů, kodérů zpráv a přenosu a protokol implementace. Obvykle elementů vazby a vazby jsou implementovány povolení kanálů pro aplikační vrstvu.  
  
 Vrstvy kanálu předá nebo přijímá zprávy do a z vrstva služby a přenáší tyto zprávy mezi koncovými body. V klientském počítači vrstvy kanálu je zásobník objektů pro vytváření kanálů, které vytvářet kanály pro koncový bod sítě. V rámci služby vrstvy kanálu je zásobník naslouchacího procesu kanálu, které přijímají kanály přijatý na koncový bod sítě.  
  
 Existují dva hlavní typy kanálů: protokol kanálů a kanály přenosu. Přenosové kanály jsou zodpovědné za skutečný přenos zprávy z koncového bodu jedna síť do jiné. Přenosové kanály musí mít výchozí kodéru zprávy a bude schopen použít kodér alternativní zprávy prostřednictvím element vazby kodéru zpráv. Kodér zprávy je zodpovědný za převod <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> na síťové vyjádření a naopak. Kanály protokolů zodpovídají za implementaci protokoly na úrovni protokolu SOAP (například WS-Security nebo WS-ReliableMessaging).  
  
 Základním požadavkem pro kanály přenosu a protokol je implementace rozhraní vyžaduje kanál. Chcete-li vytvořit vrstvu pracovní kanál musí mít vazbu objekty pro vytváření a naslouchacích procesů, a tak dále. Použít implementace kanálu z WCF musí být přidružené vazby prvků odvozených z <xref:System.ServiceModel.Channels.BindingElement> pro každý kanál a musí být prvek rozšíření související vazby pro zahrnutí do konfiguračních souborů, která je odvozena od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Jako jsme už zmínili starší, připojení prvky pro kodéry zprávy, protokol a přenosu může být implementace kanálu skládaný tvoří kanál zásobníku a mechanizmus jejich zarovnejte do uspořádané sady vazby. Vazby a prvky vazeb připojení k modelu kanál aplikační programovací model. Vaše implementace kanálu z kódu můžete použít přímo, ale pokud kodérů, přenosy a protokoly jsou implementovány jako elementů vazby nelze použít z programovací model vrstvy služby.  
  
 Podrobnosti o vývoji kanály a jejich elementů vazby najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
