---
title: Vlastní formátování zpráv
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: 9f66071d3c400ca2adc615afc7f93b2483fe2136
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795798"
---
# <a name="custom-message-formatters"></a>Vlastní formátování zpráv
Obsah zprávy je často ve formátu XML, což obvykle není vhodný formát pro aplikaci. Aplikace pracují s objekty, získávají a nastavují jejich vlastnosti. Windows Communication Foundation (WCF) používá *kontrakt dat* k převedení <xref:System.ServiceModel.Channels.Message> objektu na objekt, který snadno zpracovává aplikace. Tyto procesy se nazývají serializace a deserializace. Všimněte si, že tyto stejné výrazy se používají k popisu serializace a deserializace prováděné transportní vrstvou do a z formátu přenosu zpráv, což je nesouvisející proces.  
  
 Vlastní formátovací modul zprávy můžete použít, pokud potřebujete implementovat specializovaný převod mezi zprávami a objekty, které nemůžete provést prostřednictvím kontraktu dat. Provedete to tak, že upravíte nebo rozšíříte chování provádění konkrétní smlouvy u klienta nebo služby.  
  
## <a name="custom-message-formatters-on-the-client"></a>Vlastní formátovací moduly zpráv na klientovi  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Rozhraní definuje metody, které slouží k řízení převodu zpráv na objekty a objekty do zpráv pro klientské aplikace.  
  
 Musíte implementovat toto rozhraní. Nejprve přepište <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodu pro deserializaci zprávy. Tato metoda je volána po přijetí příchozí zprávy, ale před odesláním do klientské operace.  
  
 Dále přepište <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metodu pro serializaci objektu. Tato metoda je volána před odesláním odchozí zprávy.  
  
 Chcete-li vložit vlastní formátovací modul do aplikace služby, přiřaďte <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> objekt <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> k vlastnosti pomocí chování operace. Informace o chování najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Vlastní formátovací moduly zpráv ve službě  
 Rozhraní definuje metody, které <xref:System.ServiceModel.Channels.Message> převádějí objekt na parametry pro operaci <xref:System.ServiceModel.Channels.Message> a z parametrů do objektu v aplikaci služby. <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
  
 Musíte implementovat toto rozhraní. Nejprve přepište <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodu pro deserializaci zprávy. Tato metoda je volána po přijetí příchozí zprávy, ale před odesláním do klientské operace.  
  
 Dále přepište <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metodu pro serializaci objektu. Tato metoda je volána před odesláním odchozí zprávy.  
  
 Chcete-li vložit vlastní formátovací modul do aplikace služby, přiřaďte <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> objekt <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> k vlastnosti pomocí chování operace. Informace o chování najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Konfigurace a rozšíření modulu runtime pomocí chování](configuring-and-extending-the-runtime-with-behaviors.md)
