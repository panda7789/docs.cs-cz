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
ms.openlocfilehash: d14eb426c8e142f56d9f024dcbf37a1d2d78664d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072338"
---
# <a name="programming-pluggable-protocols"></a>Programování připojitelných protokolů
Abstraktní <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy poskytují základ pro připojitelné protokoly. Odvozené třídy pro konkrétní z <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, můžete data žádosti z internetového zdroji a čtení odpovědi bez zadání protokolu používá aplikace.  
  
 Než budete moct vytvořit protokol konkrétní <xref:System.Net.WebRequest>, je nutné zaregistrovat jeho metody Create. Použití statické <xref:System.Net.WebRequest.RegisterPrefix%28System.String%2CSystem.Net.IWebRequestCreate%29> metoda <xref:System.Net.WebRequest> k registraci <xref:System.Net.WebRequest> následné zpracování sady požadavků na konkrétní schéma Internet, schéma a server nebo do schématu, server a cestu.  
  
 Ve většině případů budete moct posílat a přijímat data pomocí metod a vlastností <xref:System.Net.WebRequest> třídy. Ale pokud potřebujete přístup k vlastnostem specifickým pro protokol, můžete přetypovat <xref:System.Net.WebRequest> k určité instanci odvozené třídy.  
  
 Abyste mohli využívat připojitelných protokolů, vaše <xref:System.Net.WebRequest> následníků musí poskytovat výchozí transakce požadavků a odpovědí, který nevyžaduje konkrétní nastavení vlastností. Například <xref:System.Net.HttpWebRequest> třídy, která implementuje <xref:System.Net.WebRequest> třídy pro protokol HTTP, poskytuje `GET` žádost ve výchozím nastavení a vrátí <xref:System.Net.HttpWebResponse> datový proud vrácený z webového serveru, který obsahuje.  
  
## <a name="see-also"></a>Viz také:

- [Odvození ze žádosti WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
- [Odvození z odpovědi WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)
- [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)
- [Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol](../../../docs/framework/network-programming/how-to-typecast-a-webrequest-to-access-protocol-specific-properties.md)
