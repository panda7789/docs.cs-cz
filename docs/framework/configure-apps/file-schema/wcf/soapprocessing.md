---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399543"
---
# <a name="soapprocessing"></a>\<soapProcessing >

Definuje chování koncového bodu klienta používaného k zařazování zpráv mezi různými typy vazeb a verzemi zpráv.

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing >**
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
  
Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|                   | Popis |
| ----------------- | ----------- |
| `processMessages` | Logická hodnota určující, zda mají být zprávy zařazeny mezi verze zprávy protokolu SOAP. |

### <a name="child-elements"></a>Podřízené prvky

Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|     | Popis |
| --- | ----------- |
| [ **\<> chování**](behavior-of-endpointbehaviors.md) | Určuje chování koncového bodu. |

## <a name="remarks"></a>Poznámky

Zpracování SOAP je proces, ve kterém se zprávy převádějí mezi verze zprávy.

Směrovací služba Windows Communication Foundation (WCF) může převést zprávy z jednoho protokolu na jiný. Pokud se verze příchozích a odchozích zpráv liší, vytvoří se nová zpráva se správnou verzí. Zpracování zpráv z jedné <xref:System.ServiceModel.Channels.MessageVersion> do druhé je provedeno vytvořením nové zprávy WCF, která obsahuje část těla a příslušné hlavičky z příchozí zprávy WCF. Hlavičky, které jsou specifické pro adresování, nebo které se rozumí na úrovni směrovače, se při konstrukci nové zprávy WCF nepoužívají, protože tato záhlaví jsou buď jiné verze (v případě hlaviček adresování), nebo se zpracovala jako součást komunikace mezi klientem a směrovačem.

Určuje, zda byla hlavička umístěna v odchozí zprávě podle toho, zda byla označena jako srozumitelná, jak byla předána prostřednictvím vrstvy příchozího kanálu. Hlavičky, které nerozumí (například vlastní hlavičky), se neodstraňují, takže je služba Směrování po zkopírování do odchozí zprávy předána. Text zprávy se zkopíruje do odchozí zprávy. Zpráva se pak pošle odchozí kanál, ve kterém se budou vytvářet a přidávat všechna záhlaví a další data obálky specifická pro daný komunikační protokol nebo přenos.

Tyto kroky zpracování se provádějí při určení chování zpracování protokolu SOAP. Toto chování soapProcessingExtension > je chování koncového bodu, které se při spuštění směrovací služby použije u všech koncových bodů klienta (odchozích). [ \<](soapprocessing.md) `true` ve `processMessages` [ \<](routing-of-servicebehavior.md) výchozím nastavení se chování > směrování vytváří a připojuje nové [ \<chování > soapProcessingExtension](soapprocessing.md) s nastavením na pro každý koncový bod klienta. Pokud máte protokol, který směrovací služba nerozumí, nebo chcete přepsat výchozí chování zpracování, můžete zakázat zpracování protokolu SOAP buď pro celou směrovací službu, nebo jenom pro konkrétní koncové body.  Chcete-li zakázat zpracování protokolu SOAP pro celou směrovací službu u všech koncových `soapProcessing` bodů, nastavte atribut [ \<chování směrování >](routing-of-servicebehavior.md) na. `false` Chcete-li vypnout zpracování SOAP pro konkrétní koncový bod, použijte toto chování a nastavte `processMessages` jeho atribut `false`na a pak připojte toto chování ke koncovému bodu, na kterém nechcete spustit výchozí kód pro zpracování.  Když chování [> Směrovánínastavísměrovacíslužbu,přeskočíopakovanéuplatněníchováníkoncovéhobodu,protožeužexistuje.\<](routing-of-servicebehavior.md)
