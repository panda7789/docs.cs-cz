---
title: <binding>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb51eb1962603439b89a203eb668dfb543049170
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271470"
---
# <a name="binding"></a>\<Vytvoření vazby >
Můžete použít `binding` element ke konfiguraci různých typů předdefinovaných vazeb, poskytnutých technologií Windows Communication Foundation (WCF).  
  
## <a name="system-provided-binding"></a>Vazeb poskytovaných systémem  
 Vazby poskytované systémem překonávají složitost systému zásobníkem zpráv WCF. Aplikace používající vazeb poskytovaných systémem nevyžadují, aby plnou kontrolu nad zásobníku. Atributy, které jsou zveřejněné na každý vazeb poskytovaných systémem jsou ty, které nejvhodnější pro scénáře použití adresy vazby.  
  
 Oddíl konfigurace pro každý vazeb poskytovaných systémem můžete definovat několik konfigurací použít ke konfiguraci vazby. Každá konfigurace je identifikován jedinečný název.  
  
 Není možné přidat do vazeb poskytovaných systémem elementy nebo atributy. Uděláte to tak, by měly implementovat vlastní vazby, jak je popsáno v části "Vlastní vazby" v tomto tématu. Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazba dokonale a přidá několik nastavení aplikace uživatele chce mít kontrolu nad.  
  
## <a name="custom-binding"></a>Vlastní vazba  
 Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF. Jednotlivé vazby definuje zásobníku zprávu zadáním elementů konfigurace pro zásobník prvky v pořadí, ve kterém se zobrazují v zásobníku. Každý prvek definuje a konfiguruje jeden prvek zásobníku. Musí existovat pouze jeden `transport` element v každé vlastní vazby. Bez tohoto elementu je neúplný zásobníkem zpráv.  
  
 Je důležité pořadí, v jakém jsou prvky uvedeny v zásobníku, protože je pořadí použití operace u zprávy. Doporučené pořadí elementů zásobníku je následující:  
  
1.  Transakce (volitelné)  
  
2.  Spolehlivé zasílání zpráv (volitelné)  
  
3.  Zabezpečení (volitelné)  
  
4.  Kodér  
  
5.  Přenos  
  
 Vlastní vazby jsou označeny jejich `name` atribut.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [Vazby](../../../docs/framework/wcf/bindings.md)
- [Vlastní vazby](../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
