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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047390"
---
# <a name="programming-pluggable-protocols"></a>Programování připojitelných protokolů
Abstraktní <xref:System.Net.WebRequest> a<xref:System.Net.WebResponse> třídy poskytují základ pro připojené protokoly. Odvozením tříd specifických pro protokol od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>může aplikace požadovat data z internetového prostředku a číst odpověď bez určení používaného protokolu.  
  
 Než budete moct vytvořit konkrétní <xref:System.Net.WebRequest>protokol, musíte zaregistrovat jeho metodu create. Použijte statickou <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> <xref:System.Net.WebRequest> metodu pro registraci <xref:System.Net.WebRequest> následníka pro zpracování sady požadavků na konkrétní internetové schéma, na schéma a Server nebo na schéma, server a cestu.  
  
 Ve většině případů budete moci odesílat a přijímat data pomocí metod a vlastností <xref:System.Net.WebRequest> třídy. Pokud však potřebujete získat přístup k vlastnostem specifickým pro protokol, můžete přetypovat <xref:System.Net.WebRequest> na konkrétní instanci odvozené třídy.  
  
 Chcete-li využít výhod protokolů pro připojení, <xref:System.Net.WebRequest> musí vaši následovníci poskytnout výchozí transakci požadavku a odpovědi, která nevyžaduje nastavení vlastností specifických pro protokol. Například <xref:System.Net.HttpWebRequest> třída, která <xref:System.Net.WebRequest> implementuje třídu `GET` pro http, poskytuje ve výchozím nastavení požadavek a vrátí objekt <xref:System.Net.HttpWebResponse> , který obsahuje datový proud vrácený z webového serveru.  
  
## <a name="see-also"></a>Viz také:

- [Odvození ze žádosti WebRequest](deriving-from-webrequest.md)
- [Odvození z odpovědi WebResponse](deriving-from-webresponse.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
- [Postupy: Přetypovat a WebRequest pro přístup k vlastnostem specifickým pro protokol](how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
