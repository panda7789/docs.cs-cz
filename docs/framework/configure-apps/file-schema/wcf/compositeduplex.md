---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 292067daacc9319c144e9d0f2da9f27ca2fcf5b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
Definuje vazbu elementu, který se používá, pokud klient musí vystavit koncový bod pro službu pro odeslání zprávy zpět do klienta.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<compositeDuplex >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|clientBaseAddress|Identifikátor URI, který nastaví adresu používající back channel v duplexní režim. Služba používá tuto adresu, aby kontaktovat a navázat spojení s klientem.<br /><br /> Pokud není tento atribut nastavit, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" se vygeneruje. Výchozí hodnota je `null`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element konfigurace se používá s přenosy, které neumožňují duplexní komunikace nativně, například HTTP. TCP, naopak umožňuje duplexní komunikace nativně a nevyžaduje použití tohoto elementu vazby pro službu k odesílání zpráv zpět do klienta.  
  
 Klient musí vystavit adresu pro službu, aby kontaktovat a navázat připojení. Tato adresa klienta poskytuje `clientBaseAddress` atribut. Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.  
  
## <a name="example"></a>Příklad  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
