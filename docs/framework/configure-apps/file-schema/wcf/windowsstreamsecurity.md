---
title: '&lt;windowsStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3ebbb7749a5ca24072e62bb482ee33abadcfb8b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsstreamsecuritygt"></a>&lt;windowsStreamSecurity&gt;
Zadejte nastavení zabezpečení systému Windows datového proudu vlastní vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<windowsStreamSecurity >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|ProtectionLevel|Definuje zabezpečení na úrovni zpráv. Podepisování zpráv snižuje riziko třetích stran manipulaci s zprávy při jejich přenosu. Během přenosu zajišťuje šifrování dat na úrovni o ochraně osobních údajů. Platné hodnoty patří:<br /><br /> -None: Žádná ochrana.<br />-Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou podepsat a zašifrovat.<br /><br /> Výchozí hodnota je EncryptAndSign.<br /><br /> Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Přenosy, které používají protokol orientované na datový proud například TCP a pojmenované kanály podpory upgrady na základě datového proudu přenosu. Konkrétně WCF poskytuje upgrady zabezpečení. Konfigurace zabezpečení tento přenos je zapouzdřené elementem tuto konfiguraci a také zobrazením [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), které mohou být konfigurovány a přidat do vlastní vazby  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
