---
title: '#direktivy pragma kontrolní součet (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 28a9ccfb9d36e648304a177294904ab1b7f18892
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44778091"
---
# <a name="pragma-checksum-c-reference"></a>#pragma – kontrolní součet (Referenční dokumentace jazyka C#)
Generuje kontrolní součty zdrojových souborů, které vám pomůže s laděním [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.  
  
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
 Řetězec šestnáctkových číslic představující počet bajtů kontrolního součtu. Musí být sudý počet šestnáctkových číslic. Lichý počet číslic za následek upozornění kompilace a direktiva se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program sady Visual Studio používá kontrolní součet abyste měli jistotu, že vždy najde správný zdroj. Kompilátor vypočítá kontrolního součtu pro zdrojový soubor a potom generuje výstup do souboru databáze (PDB) programu. Ladicí program použije soubor PDB pro porovnání, která vypočítá pro zdrojový soubor kontrolního součtu.  
  
 Toto řešení nefunguje pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekty, protože počítaný kontrolního součtu je vytvořeném zdrojovém souboru, nikoli soubor .aspx. Chcete-li vyřešit tento problém `#pragma checksum` poskytuje podporu kontrolního součtu pro [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stránky.  
  
 Při vytváření [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektu v jazyce Visual C#, vytvořeném zdrojovém souboru obsahuje kontrolní součet souboru .aspx, ze kterého se vygeneruje zdroj. Kompilátor pak tyto informace zapisuje do souboru PDB.  
  
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
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [C# Direktivy preprocesoru](../../../csharp/language-reference/preprocessor-directives/index.md)
