---
title: 'Postupy: Vyžádání webové stránky a načtení výsledků jako streamu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 74cb739d381c0b1422d9277be8c3c338a46f8fba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647421"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Postupy: Vyžádání webové stránky a načtení výsledků jako streamu
Tento příklad ukazuje, jak k vyžádání webové stránky a načtení výsledků v datovém proudu.  
  
## <a name="example"></a>Příklad  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy <xref:System.IO> a <xref:System.Net> obory názvů.  
  
## <a name="see-also"></a>Viz také:

- [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
