---
title: '#kontrolní součet pragma - odkaz C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 1bbb404e1183daa5e68e512e7439b6ae52abd605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712478"
---
# <a name="pragma-checksum-c-reference"></a>#pragma – kontrolní součet (Referenční dokumentace jazyka C#)
Generuje kontrolní součty pro zdrojové soubory, které pomáhají s laděním ASP.NET stránek.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametry  
 `"filename"`  
 Název souboru, který vyžaduje sledování změn nebo aktualizací.  
  
 `"{guid}"`  
 Globálně jedinečný identifikátor (GUID) pro algoritmus hash.  
  
 `"checksum_bytes"`  
 Řetězec šestnáctkových číslic představujících bajty kontrolního součtu. Musí to být sudý počet šestnáctkových číslic. Lichý počet číslic má za následek upozornění v době kompilace a směrnice jsou ignorovány.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program sady Visual Studio používá kontrolní součet a ujistěte se, že vždy najde správný zdroj. Kompilátor vypočítá kontrolní součet pro zdrojový soubor a potom vyzařuje výstup do souboru databáze programu (PDB). Ladicí program pak používá PDB porovnat s kontrolní mzda, která vypočítá pro zdrojový soubor.  
  
 Toto řešení nefunguje pro ASP.NET projekty, protože vypočítaný kontrolní součet je pro generovaný zdrojový soubor, nikoli pro soubor ASPX. Chcete-li tento `#pragma checksum` problém vyřešit, poskytuje podporu kontrolního součtu pro ASP.NET stránky.  
  
 Při vytváření projektu ASP.NET v jazyce Visual C# obsahuje generovaný zdrojový soubor kontrolní součet pro soubor ASPX, ze kterého je zdroj generován. Kompilátor pak zapíše tyto informace do souboru PDB.  
  
 Pokud kompilátor narazí `#pragma checksum` žádná direktiva v souboru, vypočítá kontrolní součet a zapíše hodnotu do souboru PDB.  
  
## <a name="example"></a>Příklad  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Direktivy preprocesoru jazyka C#](./index.md)
