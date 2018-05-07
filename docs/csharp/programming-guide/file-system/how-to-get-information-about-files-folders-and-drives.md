---
title: 'Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: c4f29cd2ae65fb05a2636ae3674c7ffd1613b0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)
V rozhraní .NET Framework můžete přístup k informacím systému souboru pomocí následující třídy:  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> třídy představují soubor nebo adresář a obsahovat vlastnosti, které zveřejňují mnoho atributů souborů, které jsou podporovány v systému souborů NTFS. Také obsahují metody pro otevření, zavření, přesun a odstraňování souborů a složek. Instance těchto tříd lze vytvořit pomocí předání řetězec, který představuje název souboru, složce nebo jednotce v konstruktoru:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Názvy souborů, složek nebo jednotky můžete také získat pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> a <xref:System.IO.File?displayProperty=nameWithType> tříd poskytuje statické metody pro načtení informací o adresářů a souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby přístup k informacím o soubory a složky.  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Když při zpracování řetězce cesty zadané uživatelem, by také zpracování výjimky pro tyto podmínky:  
  
-   Název souboru je poškozený. Například obsahuje neplatné znaky nebo jenom prázdný znak.  
  
-   Název souboru má hodnotu null.  
  
-   Název souboru je delší než maximální délka definovaná systémem.  
  
-   Název souboru obsahuje dvojtečku (:).  
  
 Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru, `Exists` metoda vrátí `false` bez ohledu na tom, zda cesta existuje; metoda nevyvolá výjimku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)
