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
ms.openlocfilehash: 7d5a2e3eec9b49731a09f6eb41a8d8500a59b45c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180626"
---
# <a name="using-streams-on-the-network"></a>Použití streamů v síti
Síťové prostředky jsou reprezentovány v rozhraní .NET Framework jako datové proudy. Při obecném zacházení s datovými proudy nabízí rozhraní .NET Framework následující funkce:  
  
- Běžný způsob odesílání a přijímání webových dat. Bez ohledu na skutečný obsah souboru – HTML, XML <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> nebo <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> cokoli jiného – aplikace bude používat a odesílat a přijímat data.  
  
- Kompatibilita s datovými proudy v rámci rozhraní .NET Framework. Datové proudy se používají v rámci rozhraní .NET Framework, který má bohatou infrastrukturu pro jejich zpracování. Můžete například upravit aplikaci, která čte <xref:System.IO.FileStream> data XML <xref:System.Net.Sockets.NetworkStream> z a číst data z místo toho změnou pouze několik řádků kódu, které inicializují datový proud. Hlavní rozdíly mezi **NetworkStream** třídy a jiné datové proudy jsou, že **NetworkStream** není <xref:System.Net.Sockets.NetworkStream.Seek%2A> <xref:System.Net.Sockets.NetworkStream.Position%2A> vyhledatelný, <xref:System.NotSupportedException> <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> vlastnost vždy vrátí **false**a a metody a vyvolat .  
  
- Zpracování dat při jejich příchodu. Datové proudy poskytují přístup k datům při jejich příchodu ze sítě, místo aby nutily vaši aplikaci čekat na stažení celé sady dat.  
  
 Obor <xref:System.Net.Sockets> názvů obsahuje třídu **NetworkStream,** která implementuje třídu <xref:System.IO.Stream> speciálně pro použití se síťovými prostředky. Třídy <xref:System.Net.Sockets> v oboru názvů používají třídu **NetworkStream** k reprezentaci datových proudů.  
  
 Chcete-li odesílat data do sítě <xref:System.Net.WebRequest.GetRequestStream%2A> pomocí <xref:System.Net.WebRequest>vráceného datového proudu, zavolejte na svůj . **WebRequest** odešle hlavičky požadavku na server. potom můžete odesílat data do síťového <xref:System.IO.Stream.EndWrite%2A>prostředku <xref:System.IO.Stream.Write%2A> voláním <xref:System.IO.Stream.BeginWrite%2A>, nebo metody na vrácený datový proud. Některé protokoly, například HTTP, mohou vyžadovat nastavení vlastností specifických pro protokol před odesláním dat. Následující příklad kódu ukazuje, jak nastavit vlastnosti specifické pro protokol HTTP pro odesílání dat. Předpokládá, že proměnná `sendData` obsahuje data k odeslání `sendLength` a že proměnná je počet bajtů dat k odeslání.  
  
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
  
 Chcete-li přijímat data <xref:System.Net.WebResponse.GetResponseStream%2A> ze <xref:System.Net.WebResponse>sítě, obraťte se na aplikaci . Potom můžete číst data ze síťového <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A>prostředku <xref:System.IO.Stream.Read%2A> voláním , nebo metoda na vrácený datový proud.  
  
 Při použití datových proudů ze síťových prostředků mějte na paměti následující body:  
  
- **Vlastnost CanSeek** vždy vrátí **false,** protože **NetworkStream** třídy nelze změnit pozici v datovém proudu. **Seek** a **Position** metody vyvolat **NotSupportedException**.  
  
- Při použití **WebRequest** a **WebResponse**, stream instance vytvořené voláním **GetResponseStream** jsou jen pro čtení a stream instance vytvořené voláním **GetRequestStream** jsou jen pro zápis.  
  
- Použijte <xref:System.IO.StreamReader> třídu, abyste usnadnili kódování. Následující příklad kódu používá **StreamReader** ke čtení ascii kódovaný datový proud z **WebResponse** (příklad nezobrazuje vytváření požadavku).  
  
- Volání **GetResponse** můžete blokovat, pokud síťové prostředky nejsou k dispozici. Měli byste zvážit použití asynchronní <xref:System.Net.WebRequest.BeginGetResponse%2A> ho <xref:System.Net.WebRequest.EndGetResponse%2A> požadavku s metodami a.  
  
- Volání **GetRequestStream** můžete blokovat při vytvoření připojení k serveru. Měli byste zvážit použití asynchronní požadavek <xref:System.Net.WebRequest.BeginGetRequestStream%2A> pro <xref:System.Net.WebRequest.EndGetRequestStream%2A> datový proud s a metody.  
  
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

- [Postupy:Vyžádání dat pomocí třídy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Žádosti o data](requesting-data.md)
