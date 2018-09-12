---
title: 'Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 8ebacff0f3a1704ec001e3570d0df136f54baf9d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514222"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Postupy: Získávání informací o souborech, složkách a jednotkách (Průvodce programováním v C#)
Informace o systému souborů v rozhraní .NET Framework, přístupné pomocí následující třídy:  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> a <xref:System.IO.DirectoryInfo> třídy představují soubor nebo adresář a obsahovat vlastnosti, které vystavit hodně atributů souborů, které jsou podporovány v systému souborů NTFS. Také obsahují metody pro otevření, zavření, přesunutí nebo odstranění souborů a složek. Instance těchto tříd můžete vytvořit tím, že předáte řetězec představující název souboru, složce nebo jednotce v konstruktoru:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Názvy souborů, složek nebo jednotky můžete také získat pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> a <xref:System.IO.File?displayProperty=nameWithType> třídy poskytují statické metody pro načtení informací o adresářů a souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, jak získat přístup k informacím o souborech a složkách.  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Při zpracování řetězce zadaného uživatelem cesty by měl také zpracování výjimek byly splněny následující podmínky:  
  
-   Název souboru je poškozený. Například obsahuje neplatné znaky nebo pouze prázdné znaky.  
  
-   Název souboru má hodnotu null.  
  
-   Název souboru je delší než maximální délka definovaná systémem.  
  
-   Název souboru obsahuje dvojtečku (:).  
  
 Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru `Exists` vrátí metoda `false` bez ohledu na to, zda cesta existuje, metoda nevyvolá výjimku.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO?displayProperty=nameWithType>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Systém souborů a registr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
