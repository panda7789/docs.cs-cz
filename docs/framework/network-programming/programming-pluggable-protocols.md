---
title: Programování připojitelných protokolů
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, pluggable protocols
- WebRequest class, pluggable protocols
- response to Internet request, pluggable protocols
- WebResponse class, pluggable protocols
- sending data, pluggable protocols
- network resources, pluggable protocols
- Internet, pluggable protocols
- programming pluggable protocols
- pluggable protocols, programming
- requesting data from Internet, pluggable protocols
- receiving data, pluggable protocols
- protocols, pluggable
ms.assetid: 66ef8456-7576-4e97-8956-959b216373db
ms.openlocfilehash: 94dfedd317782b9e518df02c84d9af55b1ef2b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047390"
---
# <a name="programming-pluggable-protocols"></a>Programování připojitelných protokolů
Abstraktní <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují základnu pro připojitelné protokoly. Odvozením tříd specifických pro <xref:System.Net.WebRequest> <xref:System.Net.WebResponse>protokol z aplikace a , aplikace může požadovat data z internetového prostředku a číst odpověď bez určení použitého protokolu.  
  
 Před vytvořením protokolu specifické <xref:System.Net.WebRequest>, je nutné zaregistrovat jeho Create metoda. Statickou <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> metodou registrace potomka <xref:System.Net.WebRequest> zpracování množiny požadavků na určité schéma Internetu, schématu a serveru nebo schématu, serveru a cesty.  
  
 Ve většině případů budete moci odesílat a přijímat data <xref:System.Net.WebRequest> pomocí metod a vlastností třídy. Pokud však potřebujete získat přístup k vlastnostem specifickým pro protokol, můžete typcast a <xref:System.Net.WebRequest> pro konkrétní instanci odvozené třídy.  
  
 Chcete-li využít připojitelné protokoly, potomci <xref:System.Net.WebRequest> musí poskytnout výchozí transakce požadavku a odpovědi, která nevyžaduje nastavení vlastností specifických pro protokol. Například <xref:System.Net.HttpWebRequest> třída, která implementuje třídu <xref:System.Net.WebRequest> pro `GET` PROTOKOL HTTP, <xref:System.Net.HttpWebResponse> poskytuje ve výchozím nastavení požadavek a vrací datový proud vrácený z webového serveru.  
  
## <a name="see-also"></a>Viz také

- [Odvození ze žádosti WebRequest](deriving-from-webrequest.md)
- [Odvození z odpovědi WebResponse](deriving-from-webresponse.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
- [Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
