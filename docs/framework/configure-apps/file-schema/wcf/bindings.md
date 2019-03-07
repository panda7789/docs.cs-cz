---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 7cafd8c1ba96a4fa1014f3570413b4bb83f69766
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474719"
---
# <a name="bindings"></a>\<vazby >

Můžete použít `bindings` prvek, který chcete nakonfigurovat zobrazení kolekce standardních a vlastních vazeb pro služby Windows Communication Foundation (WCF). Každá položka je `binding` element, který lze identifikovat podle jeho jedinečného `name`. Služby používají vazby jejich propojením pomocí `name`. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="system-provided-bindings"></a>vazby poskytované systémem
 
 Vazby poskytované systémem překonávají složitost systému zásobníkem zpráv WCF. Aplikace používající vazeb poskytovaných systémem nevyžadují, aby plnou kontrolu nad zásobníku. Atributy, které jsou zveřejněné na každý vazeb poskytovaných systémem jsou ty, které nejvhodnější pro scénáře použití adresy vazby.  
  
 Oddíl konfigurace pro každý vazeb poskytovaných systémem můžete definovat několik konfigurací použít ke konfiguraci vazby. Každá konfigurace je identifikován jedinečný název.  
  
 Není možné přidat do vazeb poskytovaných systémem elementy nebo atributy. Uděláte to tak, by měla implementovat vlastní vazby, jak je popsáno v [vlastní vazby](#custom-bindings) oddílu. Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazba dokonale a přidá několik nastavení aplikace uživatele chce mít kontrolu nad.  
  
 Seznam vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Vlastní vazby

 Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Jednotlivé vazby definuje zásobníku zprávu zadáním elementů konfigurace pro zásobník prvky v pořadí, ve kterém se zobrazují v zásobníku. Každý prvek definuje a konfiguruje jeden prvek zásobníku. Musí existovat pouze jeden `transport` element v každé vlastní vazby. Bez tohoto elementu je neúplný zásobníkem zpráv.  
  
 Je důležité pořadí, v jakém jsou prvky uvedeny v zásobníku, protože je pořadí použití operace u zprávy. Požadované pořadí prvků zásobníku je následující:  
  
1.  Transakce (volitelné)  
  
2.  Spolehlivé zasílání zpráv (volitelné)  
  
3.  Zabezpečení (volitelné)  
  
4.  Kodér  
  
5.  Přenos  
  
 Vlastní vazby jsou označeny jejich `name` atribut. Další informace o vlastních vazeb, naleznete v tématu [vlastních vazeb](../../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [Vazby](../../../../../docs/framework/wcf/bindings.md)  
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
