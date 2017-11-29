---
title: "Pomocí datových proudů v síti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f9e011b304a7f6c7d0d07761677c0368efcfcf4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-streams-on-the-network"></a>Pomocí datových proudů v síti
Síťové prostředky jsou v rozhraní .NET Framework vyjádřené datových proudů. Rozhraní .NET Framework tak, že obecně považuje datové proudy, nabízí následující možnosti:  
  
-   Běžný způsob, jak odesílat a přijímat Web data. Ať skutečný obsah souboru – HTML, XML nebo cokoliv jiného – vaše aplikace bude používat <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> odesílat a přijímat data.  
  
-   Kompatibilita s datovými proudy v rozhraní .NET Framework. Datové proudy se používají v rozhraní .NET Framework, který má bohaté infrastrukturu pro jejich zpracování. Například můžete upravit aplikaci, která čte data XML z <xref:System.IO.FileStream> čtení dat z <xref:System.Net.Sockets.NetworkStream> místo změnou pouze několik řádky kódu, které inicializace datového proudu. Hlavní rozdíly mezi **NetworkStream** třídy a jiné datové proudy jsou **NetworkStream** není prohledávat, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vlastnost vždy vrátí hodnotu **false**a <xref:System.Net.Sockets.NetworkStream.Seek%2A> a <xref:System.Net.Sockets.NetworkStream.Position%2A> metody throw <xref:System.NotSupportedException>.  
  
-   Zpracování dat jako jeho přijetí. Datové proudy poskytnout přístup k datům za ze sítě, nikoli vynucení aplikace čekat celá sada dat ke stažení.  
  
 <xref:System.Net.Sockets> Obor názvů obsahuje **NetworkStream** třídu, která implementuje <xref:System.IO.Stream> třída speciálně pro použití s síťovým prostředkům. Třídy v <xref:System.Net.Sockets> oboru názvů používají **NetworkStream** třída představující datových proudů.  
  
 Chcete-li odesílat data k síti pomocí vráceném datovém proudu, volejte <xref:System.Net.WebRequest.GetRequestStream%2A> na vaše <xref:System.Net.WebRequest>. **WebRequest** odešle hlaviček požadavků na server; potom může odesílat data k síťovému prostředku pomocí volání <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, nebo <xref:System.IO.Stream.Write%2A> metodu na vrácených datového proudu. Může vyžadovat některé protokoly, jako je například HTTP, můžete nastavit vlastnosti specifické pro protokol před odesláním údajů. Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro odesílání dat. Předpokládá, že proměnná `sendData` obsahuje data k odeslání a že proměnnou `sendLength` je počet bajtů dat k odeslání.  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 Chcete-li přijímat data ze sítě, volejte <xref:System.Net.WebResponse.GetResponseStream%2A> na vaše <xref:System.Net.WebResponse>. Pak můžete číst data z síťovému prostředku pomocí volání <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, nebo <xref:System.IO.Stream.Read%2A> metodu na vrácených datového proudu.  
  
 Při použití datové proudy z síťovým prostředkům, mějte na paměti následující body:  
  
-   **CanSeek** vlastnost vždy vrátí hodnotu **false** vzhledem k tomu **NetworkStream** třída nelze změnit pozici v datovém proudu. **Seek** a **pozice** metody throw **NotSupportedException**.  
  
-   Při použití **WebRequest** a **WebResponse**, stream instance vytvořená voláním **GetResponseStream** jsou jen pro čtení a stream instance vytvořená voláním  **GetRequestStream** jsou jen pro zápis.  
  
-   Použití <xref:System.IO.StreamReader> třída aby kódování snazší. Následující příklad kódu používá **StreamReader** číst stream kódováním ASCII z **WebResponse** (v příkladu nezobrazuje vytváření požadavek).  
  
-   Volání **GetResponse** můžete blokovat, pokud nejsou k dispozici síťové prostředky. Měli byste zvážit použití asynchronní požadavek s <xref:System.Net.WebRequest.BeginGetResponse%2A> a <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
-   Volání **GetRequestStream** můžete blokovat, když se vytvoří připojení k serveru. Měli byste zvážit použití asynchronní požadavek pro datový proud s <xref:System.Net.WebRequest.BeginGetRequestStream%2A> a <xref:System.Net.WebRequest.EndGetRequestStream%2A> metody.  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití třídy WebRequest Data žádosti](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Požadavek na Data](../../../docs/framework/network-programming/requesting-data.md)
