---
title: '#kontrolního součtu direktivy pragma - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 36e5602f0a0b872a4aa6cdac64b49b1d1c708795
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877525"
---
# <a name="pragma-checksum-c-reference"></a>#pragma – kontrolní součet (Referenční dokumentace jazyka C#)
Generuje kontrolní součty zdrojových souborů pro usnadnění ladění stránek ASP.NET.  
  
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
 Řetězec šestnáctkových číslic představující počet bajtů kontrolního součtu. Musí být sudý počet šestnáctkových číslic. Lichý počet číslic za následek upozornění kompilace a direktiva se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program sady Visual Studio používá kontrolní součet abyste měli jistotu, že vždy najde správný zdroj. Kompilátor vypočítá kontrolního součtu pro zdrojový soubor a potom generuje výstup do souboru databáze (PDB) programu. Ladicí program použije soubor PDB pro porovnání, která vypočítá pro zdrojový soubor kontrolního součtu.  
  
 Toto řešení pro projekty ASP.NET, nefunguje, protože počítaný kontrolního součtu je vytvořeném zdrojovém souboru, nikoli soubor .aspx. Chcete-li vyřešit tento problém `#pragma checksum` poskytuje podporu kontrolního součtu pro stránky ASP.NET.  
  
 Při vytváření projektu aplikace ASP.NET ve Vizuálu C#, obsahuje kontrolní součet souboru .aspx, ze kterého se vygeneruje zdroj vytvořeném zdrojovém souboru. Kompilátor pak tyto informace zapisuje do souboru PDB.  
  
 Pokud kompilátor narazí ne `#pragma checksum` direktivy v souboru, se vypočítá kontrolního součtu a zapíše hodnoty do souboru PDB.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
