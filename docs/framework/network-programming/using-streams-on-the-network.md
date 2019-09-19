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
ms.openlocfilehash: aa3fc56dc461d4fe22e2ff391f3561d8834128d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046880"
---
# <a name="using-streams-on-the-network"></a>Použití streamů v síti
Síťové prostředky jsou reprezentovány v .NET Framework jako datové proudy. Při obecném zpracování datových proudů nabízí .NET Framework následující možnosti:  
  
- Běžný způsob, jak odesílat a přijímat webová data. Bez ohledu na skutečný obsah souboru – HTML, XML nebo cokoli jiného – vaše aplikace bude používat <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> a <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> k posílání a přijímání dat.  
  
- Kompatibilita s datovými proudy napříč .NET Framework. Datové proudy se používají v rámci .NET Framework, které mají bohatou infrastrukturu pro jejich zpracování. Například můžete upravit aplikaci, která čte data jazyka XML z a <xref:System.IO.FileStream> <xref:System.Net.Sockets.NetworkStream> , a to tak, že změníte pouze pár řádků kódu, které inicializují datový proud. Hlavní rozdíly mezi třídou **NetworkStream** a jinými datovými proudy je, že **NetworkStream** nelze vyhledat, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vlastnost <xref:System.Net.Sockets.NetworkStream.Seek%2A> vždy vrátí **hodnotu false**a metody a <xref:System.Net.Sockets.NetworkStream.Position%2A> vyvolávají výjimku <xref:System.NotSupportedException>.  
  
- Zpracování dat při jejich doručení. Datové proudy poskytují přístup k datům, když se dorazí ze sítě, a nenutí, aby aplikace čekala na stažení celé datové sady.  
  
 Obor názvů obsahuje<xref:System.IO.Stream> třídu NetworkStream, která implementuje specifickou třídu pro použití se síťovými prostředky. <xref:System.Net.Sockets> Třídy v <xref:System.Net.Sockets> oboru názvů používají třídu **NetworkStream** k reprezentování datových proudů.  
  
 Pokud chcete odesílat data do sítě pomocí vráceného datového proudu, <xref:System.Net.WebRequest.GetRequestStream%2A> zavolejte <xref:System.Net.WebRequest>na. **WebRequest** pošle hlavičky žádosti na server. pak můžete odeslat data do síťového prostředku voláním <xref:System.IO.Stream.BeginWrite%2A>metody, <xref:System.IO.Stream.EndWrite%2A>nebo <xref:System.IO.Stream.Write%2A> na vráceném datovém proudu. Některé protokoly, například HTTP, můžou před odesláním dat vyžadovat, abyste nastavili vlastnosti specifické pro protokol. Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro protokol HTTP pro odesílání dat. Předpokládá, že proměnná `sendData` obsahuje data k odeslání a že proměnná `sendLength` je počet bajtů dat k odeslání.  
  
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
  
 Pokud chcete přijímat data ze sítě, zavolejte <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse>na. Pak můžete číst data ze síťového prostředku voláním <xref:System.IO.Stream.BeginRead%2A>metody, <xref:System.IO.Stream.EndRead%2A>nebo <xref:System.IO.Stream.Read%2A> ve vráceném datovém proudu.  
  
 Při použití datových proudů ze síťových prostředků mějte na paměti následující body:  
  
- Vlastnost **CanSeek** vždy vrací **hodnotu false** , protože třída **NetworkStream** nemůže měnit pozici v datovém proudu. Metody **hledání** a **umístění** vyvolávají výjimku **NotSupportedException**.  
  
- Když použijete **WebRequest** a **WebResponse**, instance streamu vytvořené voláním **GetResponseStream** jsou jen pro čtení a instance streamu vytvořené voláním **GetRequestStream** jsou jen pro zápis.  
  
- <xref:System.IO.StreamReader> Použijte třídu, aby bylo kódování snazší. Následující příklad kódu používá **StreamReader** ke čtení datového proudu kódovaného ASCII z **WebResponse** (příklad neukazuje vytvoření žádosti).  
  
- Volání **GetResponse** může blokovat, pokud nejsou k dispozici síťové prostředky. Měli byste zvážit použití asynchronního požadavku s <xref:System.Net.WebRequest.BeginGetResponse%2A> metodami a. <xref:System.Net.WebRequest.EndGetResponse%2A>  
  
- Volání **GetRequestStream** může blokovat při vytvoření připojení k serveru. Měli byste zvážit použití asynchronního požadavku pro datový proud s <xref:System.Net.WebRequest.BeginGetRequestStream%2A> metodami a. <xref:System.Net.WebRequest.EndGetRequestStream%2A>  
  
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
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Žádosti o data](requesting-data.md)
