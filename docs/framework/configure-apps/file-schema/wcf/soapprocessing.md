---
title: '&lt;soapProcessing&gt;'
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 1eef89290b4fda08dd7145c0615edde2fa56676c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152005"
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Definuje chování koncového bodu klient použitý k zařazování zpráv mezi jinou vazbou typy a verze zpráv.

**\<systém. ServiceModel >**   
&nbsp;&nbsp;**\<chování >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<názvy endpointBehaviors >**   
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
| `processMessages` | Logická hodnota určující, zda by měly být zařazeny zpráv mezi verzemi zprávy protokolu SOAP. |

### <a name="child-elements"></a>Podřízené prvky

Žádná

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [**\<chování >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Určuje chování koncového bodu. |

## <a name="remarks"></a>Poznámky

Zpracování SOAP je proces, ve kterém jsou zprávy převádět verze zpráv.

Směrovací služba Windows Communication Foundation (WCF) můžete převést zprávy z jednoho protokolu do jiného. Pokud verze příchozí a odchozí zprávy se liší, bude vytvořena nová zpráva správné verze. Zpracování zpráv z jednoho <xref:System.ServiceModel.Channels.MessageVersion> do druhého se provádí tak, že vytváří nové zprávy WCF, který obsahuje část textu a odpovídající záhlaví z příchozí zprávy WCF. Hlavičky, které jsou specifické pro adresování nebo, která vyplývají z úrovni směrovače nejsou použít během procesu vytváření nových zpráv WCF, protože tyto hlavičky jsou buď s jinou verzí (v případě adresování záhlaví) nebo byly zpracovány jako součást komunikace mezi klientem a směrovače.

Určuje, zda záhlaví je umístěn v odchozí zprávě se určuje podle Určuje, jestli byla označena jako chápat, jak předat prostřednictvím příchozí vrstvě kanálu. Hlavičky, které nejsou rozpoznána. (například vlastní záhlaví) se neodeberou a proto předat prostřednictvím směrovací služby byly zkopírovány na odchozí zprávu. Text zprávy je zkopírován do výstupní zprávy. Zpráva bude potom odeslaná odchozí kanál, na které všechny hlavičky a dalšími daty obálky konkrétní přejděte na tuto komunikaci protokolu/transport bude vytvořena a přidá.

Tyto kroky zpracování se použijí při zpracování SOAP chování. To [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) chování je chování koncového bodu, který se použije pro všechny koncové body klienta (odchozí) při spuštění služby směrování. výchozím [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování vytvoří a připojí nový [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) chování s `processMessages` nastavena na `true` pro každý koncový bod klienta. Pokud máte protokol, který služba Směrování neobsahuje pochopit, nebo chcete přepsat výchozí zpracování chování, můžete zakázat zpracování pro celé směrovací služba nebo pouze pro konkrétní koncové body SOAP.  Chcete-li zakázat zpracování celé směrovací služby pro všechny koncové body SOAP, nastavte `soapProcessing` atribut [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování `false`. Chcete-li vypnout zpracování pro určitý koncový bod SOAP, použijte toto chování a nastavte jeho `processMessages` atribut `false`, připojte toto chování koncového bodu nechcete, aby výchozí zpracování kódu, aby se spouštěla v.  Když [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování nastaví směrovací službou, budou přeskočeny chování koncového bodu obnovení, protože už existuje.
