---
title: "Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5652dda53a0192ce39be497b6e8ad3c97bef042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Systém souborů a registr (C# Průvodce programováním)](../../../csharp/programming-guide/file-system/index.md)
