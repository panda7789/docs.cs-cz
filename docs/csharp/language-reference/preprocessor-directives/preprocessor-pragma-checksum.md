---
title: '#Direktiva pragma kontrolní součet (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b196bbbce110acb596602fa4de2507515cdbb68
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
 Globálně jedinečný identifikátor (GUID) pro soubor.  
  
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
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
