---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735898"
---
# <a name="windowsstreamsecurity"></a>\<zabezpečení windowsstreamsecurity >
Zadejte nastavení zabezpečení Windows Stream pro vlastní vazbu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení windowsstreamsecurity >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Platné|Definuje zabezpečení na úrovni zprávy. Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy. Šifrování poskytuje během přenosu soukromí na úrovni dat. Platné hodnoty jsou následující:<br /><br /> -None: bez ochrany.<br />-Sign: zprávy jsou podepsané.<br />-EncryptAndSign: zprávy jsou podepsané a šifrované.<br /><br /> Výchozí hodnota je EncryptAndSign.<br /><br /> Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Přenosy, které používají protokol orientovaný na proud, jako je TCP a pojmenované kanály, podporují upgrady přenosu na základě datového proudu. Konkrétně WCF zajišťuje upgrady zabezpečení. Konfigurace tohoto zabezpečení přenosu se zapouzdřuje pomocí tohoto elementu konfigurace a [\<sslStreamSecurity >](sslstreamsecurity.md), která se dá nakonfigurovat a přidat k vlastní vazbě.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
