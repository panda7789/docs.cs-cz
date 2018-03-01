---
title: Vazby a prvky vazeb
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 232d2d23ea88c834d2e28bae99cd2e001f6efac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bindings-and-binding-elements"></a>Vazby a prvky vazeb
Vazby jsou kolekce elementů zvláštní konfiguraci, s názvem *elementů vazby*, které se vyhodnocují modulem runtime služby vždy, když klient nebo je vytvářen koncový bod služby. Typem a pořadím elementů vazby v rámci vazbu určuje výběr a pořadí překrývání kanály protokolu a přenosu v zásobníku kanál koncového bodu.  
  
 Vazby, zejména vazby poskytované systémem, obvykle mají také počet konfigurační vlastnosti, které odráží nejčastěji změněné vlastnosti prvky zapouzdřené vazby.  
  
 Vazba musí obsahovat přesně jeden element vazby přenosu. Každý element vazby přenosu znamená výchozí zprávu kódování vazby element, který je možné přepsat přidáním maximálně jeden element vazby pro vazby kódování zprávy. Kromě přenosu a prvky vazeb kodér vazby může obsahovat libovolný počet elementů vazby protokolu, které společně implementují funkce potřebné pro služby a odeslat zprávu protokolu SOAP z jednoho koncového bodu do jiného. Podrobnosti najdete v tématu [pomocí vazby na konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Rozšiřování vazeb a elementů vazby  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zahrnuje vazby poskytované systémem, které se týkají širokou škálu scénářů. (Další informace najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).) Může se stát, ale když potřebujete vytvořit a použít vazbu, která není součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Následující scénáře vyžadují vytvoření novou vazbu.  
  
-   Pokud chcete používat nové prvku vazby (například nový přenos, kódování nebo element vazby protokolu), musíte vytvořit novou vazbu, která obsahuje daný element vazby. Například, pokud jste přidali vlastní `UdpTransportBindingElement` pro přenos UDP, by je potřeba vytvořit novou vazbu, aby jeho používání. Informace o provádění toto chování pomocí <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> zadejte najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
-   Ke konfiguraci existující prvky vazeb způsobem, který vazby poskytované systémem není vystavit na veřejné vlastnosti. Například musíte vytvořit novou vazbu a změňte pořadí, ve které podepisování a šifrování operací. Informace o provádění toto chování najdete v tématu [postupy: přizpůsobení vazbu System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
-   Chcete-li vytvořit podnikové standardní vazby, které zveřejňují pouze možnosti konkrétní konfigurace. Například vytvořit pro vaši společnost jeho variantě <xref:System.ServiceModel.WSHttpBinding> pro vaší společnosti, ve kterém nejde vypnout zabezpečení, vytvořte novou vazbu, který se chová stejně jako <xref:System.ServiceModel.WSHttpBinding>, ale vždy na zabezpečení. Podrobnosti najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
-   K provedení některých přizpůsobení metadat, obvykle ale nemusí nutně jít pro konfiguraci nebo použít některé prvku vlastní vazby. Další informace o zajištění podpory metadata pro vazby a prvky vazeb najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
-  
  
## <a name="channels-bindings-and-binding-elements"></a>Kanály, vazby a prvky vazeb  
 Vazby a prvky vazeb se připojení mezi programovací model aplikace, které zahrnují atributy a chování, a model kanálu, který obsahuje objekty pro vytváření a naslouchací procesy, kodéry zprávy a přenos a protokol implementace. Prvky vazeb a vazeb se obvykle implementují Povolit kanály, které má být používána aplikační vrstvu.  
  
 Vrstvy kanálu předá nebo přijímá zprávy do a z vrstvy služby a je určena k přenosu těchto zpráv mezi koncovými body. V klientovi je vrstvy kanálu zásobník objektů Factory channel, které vytvářejí kanály pro koncový bod sítě. Na službě je vrstvy kanálu zásobníku naslouchacího procesu kanálu, které přijímají kanály přijme koncový bod sítě.  
  
 Existují dvě obecné typy kanály: protokolu kanálů a kanály přenosu. Přenosové kanály jsou zodpovědní za skutečné přenos zpráv z jedné sítě koncového bodu do jiného. Přenosové kanály musí mít výchozí kodéru zprávy a musí být možné použít kodér alternativní zprávy prostřednictvím element zpráva kodér vazby. Kodér zpráv je zodpovědná za měnící <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> do síťové vyjádření a naopak. Kanály protokolů jsou zodpovědní za implementaci protokolů SOAP úrovně (například WS-zabezpečení nebo protokolu WS-ReliableMessaging).  
  
 Primární požadavek na přenos a protokol kanálů je implementovaly rozhraní požadované kanálu. K vytvoření vrstvy kanálu pracovní musí mít přidružené objekty pro vytváření a naslouchací procesy a tak dále. Použití kanálu implementace z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je potřeba prvky přidružené vazeb odvozené z <xref:System.ServiceModel.Channels.BindingElement> pro každý kanál a mělo by být element rozšíření související vazby pro zahrnutí do konfigurační soubory, které je odvozena z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Jako uvedených starší, závazné prvky pro zprávu kodéry, protokol a přenosu může být implementace kanál skládaný k vytvoření kanálu zásobníku a mechanismus zarovnejte je do seřazené sady je vazba. Vazby a prvky vazeb připojení k modelu kanálu programovací model aplikace. Můžete použít vaší implementace kanál z kódu přímo, ale pokud kodéry přenosy a protokoly jsou implementované jako elementů vazby nelze použít z programovací model vrstvy služby.  
  
 Podrobnosti o vývoji kanály a jejich elementů vazby najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).
