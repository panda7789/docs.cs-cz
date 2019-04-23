---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159845"
---
# <a name="compositeduplex"></a>\<compositeDuplex>
Definuje prvek vazby, který se používá, když klient musí vystavit koncový bod služby umožňující odesílání zpráv zpět klientovi.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<compositeDuplex>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientBaseAddress|Identifikátor URI, který nastaví adresu zpětného kanálu v duplexním režimu. Služba používá tuto adresu kontaktovat a naváže připojení klienta.<br /><br /> Pokud není tento atribut nastaven, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" je generován. Výchozí hodnota je `null`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace se používá s přenosy, které neumožňují duplexní komunikaci nativně, například HTTP. TCP, naopak umožňuje nativně duplexní komunikaci a nevyžaduje použití tohoto elementu vazby pro služby umožňující odesílání zpráv zpět klientovi.  
  
 Klient musí vystavit adresu pro službu kontaktovat a navázat připojení. Tato adresa klienta poskytuje `clientBaseAddress` atribut. Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.  
  
## <a name="example"></a>Příklad  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
