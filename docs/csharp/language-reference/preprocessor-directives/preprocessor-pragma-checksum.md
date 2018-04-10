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
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 Při vytváření [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektu v [!INCLUDE[csprcs](~/includes/csprcs-md.md)], vytvořeném zdrojovém souboru obsahuje kontrolního součtu pro soubor .aspx, ze které se generuje zdroji. Kompilátor pak zapíše tyto informace do souboru PDB.  
  
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [C# direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
