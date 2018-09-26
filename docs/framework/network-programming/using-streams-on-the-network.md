---
title: Použití streamů v síti
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1157fd8772546a1e34343bcf05ac40ca8ad592a5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080978"
---
# <a name="using-streams-on-the-network"></a>Použití streamů v síti
Síťové prostředky jsou reprezentovány v rozhraní .NET Framework jako datové proudy. Rozhraní .NET Framework pomocí zpracování datových proudů obecně, nabízí následující možnosti:  
  
-   Běžný způsob odesílání a příjem dat z webu. Bez ohledu skutečný obsah souboru – HTML, XML nebo cokoli jiného, bude aplikace používat <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> odesílat a přijímat data.  
  
-   Kompatibilita s datovými proudy v rozhraní .NET Framework. Datové proudy se používají v rozhraní .NET Framework, která má bohaté infrastrukturu pro jejich zpracování. Například můžete upravit aplikaci, která čte data XML z <xref:System.IO.FileStream> číst data z <xref:System.Net.Sockets.NetworkStream> místo toho změnou jen několika řádků kódu, které inicializovat datový proud. Hlavní rozdíly mezi **NetworkStream** třídy a jiné datové proudy, které **NetworkStream** neumožňuje vyhledávání, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vždy vrátí vlastnost **false**a <xref:System.Net.Sockets.NetworkStream.Seek%2A> a <xref:System.Net.Sockets.NetworkStream.Position%2A> vyvolání metody <xref:System.NotSupportedException>.  
  
-   Zpracování dat, protože doručena. Datové proudy poskytují přístup k datům, jako je e-mailu ze sítě, místo vynucení aplikace čekat celá sada dat ke stažení.  
  
 <xref:System.Net.Sockets> Obsahuje obor názvů **NetworkStream** třídu, která implementuje <xref:System.IO.Stream> třídy speciálně pro použití se síťovým prostředkům. Třídy v <xref:System.Net.Sockets> oboru názvů, použijte **NetworkStream** pro reprezentaci datových proudů.  
  
 Chcete-li odesílat data do sítě pomocí vrácený datový proud, zavolejte <xref:System.Net.WebRequest.GetRequestStream%2A> na vaše <xref:System.Net.WebRequest>. **WebRequest** odešle hlavičky požadavku na server, pak může odesílat data k síťovému prostředku pomocí volání <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, nebo <xref:System.IO.Stream.Write%2A> metoda ve vráceném datovém proudu. Může vyžadovat některé protokoly, jako je například HTTP, můžete nastavit vlastnosti specifické pro protokol před odesláním údajů. Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro protokol HTTP pro odesílání dat. Předpokládá, že proměnné `sendData` obsahuje data k odeslání a že je proměnná `sendLength` je počet bajtů dat k odeslání.  
  
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
  
 Chcete-li přijímat data ze sítě, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A> na vaše <xref:System.Net.WebResponse>. Potom může číst data ze síťových prostředků pomocí volání <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, nebo <xref:System.IO.Stream.Read%2A> metoda ve vráceném datovém proudu.  
  
 Při použití datových proudů z síťovým prostředkům, mějte na paměti následující body:  
  
-   **CanSeek** vždy vrátí vlastnost **false** od **NetworkStream** třídy nelze změnit pozici v datovém proudu. **Seek** a **pozice** vyvolání metody **NotSupportedException**.  
  
-   Při použití **WebRequest** a **WebResponse**, Streamovat instancí vytvořených voláním **GetResponseStream** jsou jen pro čtení a instance vytvořené pomocí volání datovýproudstream **GetRequestStream** jsou jen pro zápis.  
  
-   Použití <xref:System.IO.StreamReader> třídy, aby bylo snazší kódování. Následující příklad kódu používá **StreamReader** přečíst kódováním ASCII stream z **WebResponse** (v příkladu se nezobrazují žádost o).  
  
-   Volání **GetResponse** může blokovat, pokud nejsou k dispozici síťové prostředky. Měli byste zvážit použití asynchronního požadavku s <xref:System.Net.WebRequest.BeginGetResponse%2A> a <xref:System.Net.WebRequest.EndGetResponse%2A> metody.  
  
-   Volání **GetRequestStream** můžete blokovat, když se vytvoří připojení k serveru. Měli byste zvážit použití asynchronního požadavku pro datový proud s <xref:System.Net.WebRequest.BeginGetRequestStream%2A> a <xref:System.Net.WebRequest.EndGetRequestStream%2A> metody.  
  
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
 [Postupy:Vyžádání dat pomocí třídy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
