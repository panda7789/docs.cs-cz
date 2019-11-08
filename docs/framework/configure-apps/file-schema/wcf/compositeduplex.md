---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736787"
---
# <a name="compositeduplex"></a>\<compositeDuplex >
Definuje prvek vazby, který se používá v případě, že klient musí vystavit koncový bod, který bude službě odesílat zprávy zpět do klienta.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientBaseAddress|Identifikátor URI, který nastaví adresu back-Channel v duplexovém režimu. Služba používá tuto adresu k tomu, aby kontaktovala a navázala spojení s klientem.<br /><br /> Pokud tento atribut není nastaven, je vygenerována výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`". Výchozí hodnota je `null`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace se používá s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP. Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.  
  
 Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení. Tato adresa klienta je poskytována atributem `clientBaseAddress`. Všimněte si, že Windows Communication Foundation (WCF) automaticky vygeneruje ClientBaseAddress, pokud ho uživatel explicitně nenastaví.  
  
## <a name="example"></a>Příklad  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
