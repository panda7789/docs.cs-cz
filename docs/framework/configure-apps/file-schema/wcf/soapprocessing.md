---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e83bfc0f868526ad5366032f08956a6c14a1056
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Definuje chování klienta endpoint použitý k zařazování zprávy mezi jinou vazbou typy a verze zprávy.

**\<systém. ServiceModel >**   
&nbsp;&nbsp;**\<chování >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chování >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**

## <a name="syntax"></a>Syntaxe

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|                   | Popis |
| ----------------- | ----------- |
| `processMessages` | Logická hodnota, která určuje, zda by měl být zařazen zpráv mezi verzemi protokolu SOAP zprávy. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [**\<chování >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Určuje chování koncového bodu. |

## <a name="remarks"></a>Poznámky

Zpracování protokolu SOAP je proces, kde se převedou zpráv mezi verzemi zprávy.

[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Směrovací služby můžete převést zprávy z jednoho protokolu na jiný. Pokud příchozí a odchozí verze zprávy liší, je vytvořit novou zprávu správnou verzi. Zpracování zpráv z jednoho <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` do jiného provádí vytváření nové [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprávu, která obsahuje část textu a relevantní záhlaví z příchozích [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprávy. Hlavičky, které jsou specifické pro adresování nebo které jsou pochopeny na úrovni směrovače, nejsou použít během vytváření nové zprávy WCF, protože tato záhlaví, jsou jiné verzi (v případě adresování hlavičky) nebo byly zpracovány jako součást komunikace mezi klientem a směrovači.

Jestli je umístěn hlavičku odchozí zprávy je dáno, jestli byla označena jako porozumění, jako je předána příchozí vrstvy kanálu. Hlavičky, které nejsou porozuměl (například vlastní hlavičky) nejsou odebrány a proto procházet služba Směrování podle byly zkopírovány na odchozí zprávy. Tělo zprávy se zkopíruje na odchozí zprávy. Odchozí kanál potom odeslaná zpráva, na kterém všechny hlavičky a další data obálky konkrétní přejděte na tuto komunikaci protokol nebo přenos vytvořit a přidat.

Tyto kroky zpracování se provede při zpracování protokolu SOAP chování je zadán. To [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) chování je chování koncového bodu, který se použije pro všechny koncové body klienta (odchozí) při spuštění služby směrování. výchozí [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování vytvoří a připojí nový [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) chování s `processMessages` nastavena na `true` pro každou koncový bod klienta. Pokud máte protokol, který směrovací služby nemá pochopit, nebo chcete přepsat výchozí chování pro zpracování, můžete zakázat zpracování pro celý směrovací služby nebo jenom pro konkrétní koncových bodů protokolu SOAP.  Chcete-li zakázat zpracování pro službu celý směrování na všechny koncové body SOAP, nastavte `soapProcessing` atribut [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování `false`. Chcete-li vypnout zpracování pro konkrétní koncový bod protokolu SOAP, použijte toto chování a nastavit jeho `processMessages` atribut `false`, toto chování přiřadit nechcete zpracování kód pro spuštění na výchozí koncový bod.  Když [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování nastaví službu směrování, přeskočí opětovné použití chování koncový bod, protože již existuje.
