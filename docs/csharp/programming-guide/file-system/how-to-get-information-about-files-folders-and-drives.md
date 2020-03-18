---
title: Jak získat informace o souborech, složkách a jednotkách – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705207"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Jak získat informace o souborech, složkách a jednotkách (Průvodce programováním jazyka C#)
V rozhraní .NET Framework můžete získat přístup k informacím o systému souborů pomocí následujících tříd:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> Třídy <xref:System.IO.DirectoryInfo> a představují soubor nebo adresář a obsahují vlastnosti, které zveřejňují mnoho atributů souborů podporovaných systémem souborů NTFS. Obsahují také metody pro otevírání, zavírání, přesouvání a odstraňování souborů a složek. Instance těchto tříd můžete vytvořit předáním řetězce, který představuje název souboru, složky nebo jednotky do konstruktoru:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Názvy souborů, složek nebo jednotek můžete získat <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>také <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>pomocí volání aplikace , a .  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> Třídy <xref:System.IO.File?displayProperty=nameWithType> a poskytují statické metody pro načítání informací o adresářích a souborech.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby přístupu k informacím o souborech a složkách.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Při zpracování řetězců cesty zadané uživatelem byste měli také zpracovávat výjimky pro následující podmínky:  
  
- Název souboru je poškozen. Obsahuje například neplatné znaky nebo pouze prázdné znaky.  
  
- Název souboru je null.  
  
- Název souboru je delší než maximální délka definovaná systémem.  
  
- Název souboru obsahuje dvojtečku (:).  
  
 Pokud aplikace nemá dostatečná oprávnění ke čtení `Exists` zadaného `false` souboru, metoda vrátí bez ohledu na to, zda existuje cesta; metoda nevyvolá výjimku.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>
- [Programovací příručka jazyka C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
