---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399543"
---
# \<soapProcessing>

Definuje chování koncového bodu klienta používaného k zařazování zpráv mezi různými typy vazeb a verzemi zpráv.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
  
Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|                   | Description |
| ----------------- | ----------- |
| `processMessages` | Logická hodnota určující, zda mají být zprávy zařazeny mezi verze zprávy protokolu SOAP. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|     | Description |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | Určuje chování koncového bodu. |

## <a name="remarks"></a>Poznámky

Zpracování SOAP je proces, ve kterém se zprávy převádějí mezi verze zprávy.

Směrovací služba Windows Communication Foundation (WCF) může převést zprávy z jednoho protokolu na jiný. Pokud se verze příchozích a odchozích zpráv liší, vytvoří se nová zpráva se správnou verzí. Zpracování zpráv z jedné <xref:System.ServiceModel.Channels.MessageVersion> do druhé je provedeno vytvořením nové zprávy WCF, která obsahuje část těla a příslušné hlavičky z příchozí zprávy WCF. Hlavičky, které jsou specifické pro adresování nebo které jsou srozumitelné na úrovni směrovače, se nepoužívají během vytváření nové zprávy WCF, protože tato záhlaví jsou buď jiné verze (v případě hlaviček adresování), nebo jsou zpracovaná jako součást komunikace mezi klientem a směrovačem.

Určuje, zda byla hlavička umístěna v odchozí zprávě podle toho, zda byla označena jako srozumitelná, jak byla předána prostřednictvím vrstvy příchozího kanálu. Hlavičky, které nerozumí (například vlastní hlavičky), se neodstraňují, takže je služba Směrování po zkopírování do odchozí zprávy předána. Text zprávy se zkopíruje do odchozí zprávy. Zpráva se pak pošle odchozí kanál, ve kterém se budou vytvářet a přidávat všechna záhlaví a další data obálky specifická pro daný komunikační protokol nebo přenos.

Tyto kroky zpracování se provádějí při určení chování zpracování protokolu SOAP. Toto [\<soapProcessingExtension>](soapprocessing.md) chování je chování koncového bodu, které se použije u všech koncových bodů klienta (odchozích) při spuštění směrovací služby. ve výchozím nastavení [\<routing>](routing-of-servicebehavior.md) chování vytvoří a připojí nové [\<soapProcessingExtension>](soapprocessing.md) chování s `processMessages` nastavením na `true` pro každý koncový bod klienta. Pokud máte protokol, který směrovací služba nerozumí, nebo chcete přepsat výchozí chování zpracování, můžete zakázat zpracování protokolu SOAP buď pro celou směrovací službu, nebo jenom pro konkrétní koncové body.  Chcete-li zakázat zpracování protokolu SOAP pro celou směrovací službu ve všech koncových bodech, nastavte `soapProcessing` atribut [\<routing>](routing-of-servicebehavior.md) chování na hodnotu `false` . Chcete-li vypnout zpracování SOAP pro konkrétní koncový bod, použijte toto chování a nastavte jeho `processMessages` atribut na `false` a pak připojte toto chování ke koncovému bodu, na kterém nechcete spustit výchozí kód pro zpracování.  Když [\<routing>](routing-of-servicebehavior.md) chování nastaví směrovací službu, přeskočí opakované použití chování koncového bodu, protože již existuje.
