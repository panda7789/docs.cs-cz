---
title: "Modulární protokoly programování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 51d9b6e444cfa49bfbf7854ee7f33f5a45d80e31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="programming-pluggable-protocols"></a>Modulární protokoly programování
Abstraktní <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují základ pro připojitelné protokoly. Odvozené třídy specifické pro protokol z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, můžete data žádosti z internetových prostředků a přečíst odpověď bez zadání protokol používá aplikace.  
  
 Před vytvořením konkrétního protokolu <xref:System.Net.WebRequest>, je nutné zaregistrovat jeho metody Create. Použít statickou <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metodu <xref:System.Net.WebRequest> k registraci <xref:System.Net.WebRequest> následné zpracování sadu požadavků na konkrétní schéma Internet, schéma a server nebo do schématu, serveru a cestu.  
  
 Ve většině případů bude moct posílat a přijímat data pomocí metody a vlastnosti <xref:System.Net.WebRequest> třídy. Ale pokud budete potřebovat přístup k vlastnosti specifické pro protokol, vám může přiřazení typu <xref:System.Net.WebRequest> ke konkrétní instanci odvozené třídy.  
  
 Chcete využít výhod modulární protokoly, vaše <xref:System.Net.WebRequest> následníky musíte zadat výchozí požadavků a odpovědí transakci, která nevyžaduje vlastnosti specifické pro protokol nastavení. Například <xref:System.Net.HttpWebRequest> třídy, které implementuje <xref:System.Net.WebRequest> třídy pro protokol HTTP, poskytuje `GET` požadavku ve výchozím nastavení a vrátí <xref:System.Net.HttpWebResponse> obsahující datový proud vrácený z webového serveru.  
  
## <a name="see-also"></a>Viz také  
 [Odvozování z WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)  
 [Odvozování z WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)  
 [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)  
 [Postupy: přiřazení typu WebRequest na specifické vlastnosti protokolu přístupu](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
