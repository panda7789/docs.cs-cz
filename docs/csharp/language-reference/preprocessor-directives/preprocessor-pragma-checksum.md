---
title: '#Direktiva pragma kontrolní součet (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 603b56325d7b690a153bd7db41f34621675a4ba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285691"
---
# <a name="pragma-checksum-c-reference"></a>#pragma – kontrolní součet (Referenční dokumentace jazyka C#)
Generuje kontrolní součty pro zdrojové soubory, které pomáhají s laděním [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parametry  
 `"filename"`  
 Název souboru, který vyžaduje monitorování pro změny nebo aktualizace.  
  
 `"{guid}"`  
 Globálně jedinečný identifikátor (GUID) pro algoritmus hash.  
  
 `"checksum_bytes"`  
 Řetězec šestnáctkových číslic představující bajtů kontrolního součtu. Musí být sudé číslo šestnáctkových číslic. Lichý počet číslic za následek upozornění kompilaci a direktiva se ignorují.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program Visual Studio používá kontrolní součet a ujistěte se, že vždy vyhledá správné zdroje. Kompilátor vypočítá kontrolní součet u zdrojového souboru a potom vydá výstup do souboru databáze (PDB) programu. Ladicí program pak použije PDB pro porovnání, které vrací pro zdrojový soubor kontrolního součtu.  
  
 Toto řešení nefunguje pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekty, protože počítaný kontrolního součtu je vytvořeném zdrojovém souboru, nikoli soubor .aspx. Chcete-li vyřešit tento problém `#pragma checksum` poskytuje podporu kontrolního součtu pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.  
  
 Při vytváření [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekt v jazyce Visual C#, vytvořeném zdrojovém souboru obsahuje kontrolního součtu pro soubor .aspx, ze které se generuje zdroji. Kompilátor pak zapíše tyto informace do souboru PDB.  
  
 Pokud ne, zaznamená kompilátor `#pragma checksum` direktivy v souboru, se vypočítá kontrolního součtu a zapisuje do souboru PDB hodnota.  
  
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
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
