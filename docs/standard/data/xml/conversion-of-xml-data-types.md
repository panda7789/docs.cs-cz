---
title: Převod datových typů XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b6e6f2c4b28e9220727bf0fe1a958a7b69111571
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202164"
---
# <a name="conversion-of-xml-data-types"></a>Převod datových typů XML
Většina metod nalezených ve třídě **XmlConvert** slouží k převodu dat mezi řetězci a formátů silného typu. Metody jsou nezávislé na národním prostředí. To znamená, že při konverzi neberou v úvahu žádná nastavení národního prostředí.  
  
## <a name="reading-string-as-types"></a>Čtení řetězce jako typů  
 Následující příklad přečte řetězec a převede ho na typ **DateTime** .  
  
 S ohledem na následující vstup XML:  
  
 **Vstup**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Tento kód převede řetězec na formát **data a času** :  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a>Zápis řetězců jako typů  
 Následující příklad přečte typ **Int32** a převede ho na řetězec.  
  
 S ohledem na následující vstup XML:  
  
 **Vstup**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Tento kód převede typ **Int32** na **řetězec**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Viz také

- [Převádění řetězců na datové typy rozhraní .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [Převádění typů rozhraní .NET Framework na řetězce](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
