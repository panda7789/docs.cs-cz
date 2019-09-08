---
title: Vazby a prvky vazeb
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: d4d69495c1ae19b6799fdb9981f6b332cc2580d3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795849"
---
# <a name="bindings-and-binding-elements"></a>Vazby a prvky vazeb
Vazby jsou kolekce speciálních elementů konfigurace, které se nazývají *prvky vazby*, které jsou vyhodnocovány modulem runtime služby při vytváření koncového bodu klienta nebo služby. Typ a pořadí prvků vazby v rámci vazby Určuje výběr a pořadí skládání protokolů a přenosových kanálů v zásobníku kanálu koncového bodu.  
  
 Vazby, zejména systémově poskytované vazby, mají obvykle také množství vlastností konfigurace, které odráží nejčastěji změněné vlastnosti zapouzdřených prvků vazby.  
  
 Vazba musí obsahovat právě jeden element transportních vazeb. Každý element vazby přenosu implikuje výchozí element vazby kódování zprávy, který může být přepsán přidáním maximálně jednoho prvku vazby kódování zprávy do vazby. Kromě prvků pro přenos a kodér vazby může vazba obsahovat libovolný počet prvků vazby protokolu, které společně implementují funkcionalitu nutnou ke službě a odeslání zprávy protokolu SOAP z jednoho koncového bodu do druhého. Podrobnosti najdete v tématu [použití vazeb ke konfiguraci služeb a klientů](../using-bindings-to-configure-services-and-clients.md).  
  
## <a name="extending-bindings-and-binding-elements"></a>Rozšíření vazeb a elementů vazby  
 Windows Communication Foundation (WCF) zahrnuje vazby poskytované systémem, které pokrývají široké spektrum scénářů. (Další informace najdete v tématu [vazby poskytované systémem](../system-provided-bindings.md).) Mohou však nastat situace, kdy potřebujete vytvořit a použít vazbu, která není součástí služby WCF. Následující scénáře vyžadují vytvoření nové vazby.  
  
- Chcete-li použít nový prvek vazby (například nový přenos, kódování nebo element vazby protokolu), je nutné vytvořit novou vazbu, která bude obsahovat prvek vazby. Pokud jste například přidali vlastní `UdpTransportBindingElement` přenos UDP, budete muset vytvořit novou vazbu, abyste ji mohli používat. Informace o tom, jak toto chování používat <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> , naleznete v tématu [Custom Bindings](custom-bindings.md).  
  
- Chcete-li konfigurovat existující prvky vazby způsobem, že vazby poskytnuté systémem nejsou vystavení pro veřejné vlastnosti. Například je třeba vytvořit novou vazbu pro změnu pořadí, ve kterém se provádí operace podepisování a šifrování. Informace o tom, jak toto chování provést [, najdete v tématu How to: Přizpůsobení vazby](how-to-customize-a-system-provided-binding.md)poskytnuté systémem.  
  
- Pro vytvoření podnikových standardních vazeb, které zveřejňují pouze konkrétní možnosti konfigurace. Pokud například chcete vytvořit pro vaši společnost variantu <xref:System.ServiceModel.WSHttpBinding> pro vaši společnost, ve které zabezpečení nelze zakázat, vytvořte novou vazbu, která se bude <xref:System.ServiceModel.WSHttpBinding>chovat jako, ale vždy se zabezpečením. Podrobnosti najdete v tématu [vytváření uživatelsky definovaných vazeb](creating-user-defined-bindings.md).  
  
- K provedení některých přizpůsobení metadat, obvykle ale nikoli nutně ke konfiguraci nebo použití některé vlastní prvky vazby. Další informace o poskytování podpory metadat pro vazby a prvky vazby naleznete v tématu [podpora konfigurace a metadat](configuration-and-metadata-support.md).  

## <a name="channels-bindings-and-binding-elements"></a>Kanály, vazby a prvky vazby  
 Vazby a prvky vazby jsou propojení mezi programovacím modelem aplikace, což zahrnuje atributy a chování a model kanálu, který zahrnuje továrny a naslouchací procesy, kodéry zpráv a přenos a protokol. implementaci. Prvky vazby a vazby jsou obvykle implementovány, aby umožňovaly použití kanálů aplikační vrstvou.  
  
 Vrstva kanálu odpíná nebo přijímá zprávy do a z vrstvy služby a přesměruje tyto zprávy mezi koncovými body. V klientovi je vrstva kanálu zásobníkem kanálů kanálu, které vytvářejí kanály pro koncový bod sítě. V rámci služby je vrstva kanálu zásobníkem naslouchacích kanálů, které přijímají kanály přijaté v síťovém koncovém bodě.  
  
 Existují dva obecné typy kanálů: kanály protokolu a transportní kanály. Přenosové kanály zodpovídá za skutečný přenos zprávy z jednoho koncového bodu sítě do druhého. Přenosové kanály musí mít výchozí kodér zprávy a měly by být schopné použít alternativní kodér zpráv dodaný prostřednictvím elementu vazby kodéru zprávy. Kodér zpráv je zodpovědný za to, že <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> je k disdobu spojení s vodiči a naopak. Kanály protokolu jsou zodpovědné za implementaci protokolů na úrovni protokolu SOAP (například WS-Security nebo WS-ReliableMessaging).  
  
 Hlavním požadavkem na přenosové a protokolové kanály je, že implementují požadovaná rozhraní kanálů. Chcete-li vytvořit vrstvu pracovního kanálu, musí mít přidružené továrny a naslouchací procesy atd. Aby bylo možné použít implementace kanálů ze služby WCF, musí být přidružené prvky vazby odvozené z <xref:System.ServiceModel.Channels.BindingElement> pro každý kanál a měl by existovat související element rozšíření vazby pro zahrnutí do konfiguračních souborů, které jsou odvozeny z <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 Jak bylo zmíněno dříve, prvky vazby pro implementaci kodérů zpráv, protokolů a přenosového kanálu lze navrstvit tak, aby tvořily zásobník kanálu a mechanismus, který je zařadí do seřazené sady, je vazba. Vazby a prvky vazby spojují programovací model aplikace s modelem kanálu. Můžete použít implementace kanálů přímo z kódu, ale pokud nejsou kodéry, přenosy a protokoly implementovány jako prvky vazby, nelze je použít z programovacího modelu vrstvy služby.  
  
 Podrobnosti o vývoji kanálů a jejich elementů vazby naleznete v tématu [rozšíření vrstvy kanálu](extending-the-channel-layer.md).
