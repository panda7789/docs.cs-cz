---
description: '#pragma Checksum – reference jazyka C#'
title: '#pragma Checksum – reference jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 60c491000337fd50da217e97054e86faccb2e7d7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137978"
---
# <a name="pragma-checksum-c-reference"></a>#pragma – kontrolní součet (Referenční dokumentace jazyka C#)
Vygeneruje kontrolní součty pro zdrojové soubory, které pomáhají s laděním ASP.NET stránek.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Parametry  
 `"filename"`  
 Název souboru, který vyžaduje monitorování pro změny nebo aktualizace.  
  
 `"{guid}"`  
 Globálně jedinečný identifikátor (GUID) pro algoritmus hash.  
  
 `"checksum_bytes"`  
 Řetězec hexadecimálních číslic reprezentujících bajty kontrolního součtu. Musí se jednat o sudý počet šestnáctkových číslic. Lichý počet číslic má za následek upozornění v době kompilace a direktiva se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program sady Visual Studio používá kontrolní součet k tomu, aby se ujistil, že vždy najde správný zdroj. Kompilátor vypočítá kontrolní součet pro zdrojový soubor a poté vygeneruje výstup do souboru programu databáze (PDB). Ladicí program pak pomocí PDB porovná s kontrolním součtem, který počítá pro zdrojový soubor.  
  
 Toto řešení nefunguje pro projekty ASP.NET, protože vypočtený kontrolní součet je pro generovaný zdrojový soubor, nikoli soubor. aspx. Pro vyřešení tohoto problému `#pragma checksum` poskytuje podporu kontrolního součtu pro stránky ASP.NET.  
  
 Při vytváření projektu ASP.NET v jazyce Visual C# vygenerovaný zdrojový soubor obsahuje kontrolní součet pro soubor. aspx, ze kterého je zdroj generován. Kompilátor potom tyto informace zapíše do souboru PDB.  
  
 Pokud kompilátor v souboru nenalezne žádnou `#pragma checksum` direktivu, vypočítá kontrolní součet a zapíše hodnotu do souboru PDB.  
  
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

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [C# – direktivy preprocesoru](./index.md)
