---
title: Jak získat informace o souborech, složkách a jednotkách – Průvodce programováním v C#
description: Naučte se, jak získat informace o souborech, složkách a jednotkách. Podívejte se na příklad kódu a další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: f696cd90f197bede1a64949d211a563ce9a18376
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299926"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Jak získat informace o souborech, složkách a jednotkách (Průvodce programováním v C#)
V rozhraní .NET můžete získat přístup k informacím o systému souborů pomocí následujících tříd:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo>Třídy a <xref:System.IO.DirectoryInfo> představují soubor nebo adresář, který obsahuje vlastnosti, které zveřejňují mnoho atributů souboru, které jsou podporovány systémem souborů NTFS. Obsahují také metody otevírání, zavírání, přesouvání a odstraňování souborů a složek. Instance těchto tříd lze vytvořit předáním řetězce, který představuje název souboru, složky nebo jednotky v konstruktoru do konstruktoru:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Můžete také získat názvy souborů, složek nebo jednotek pomocí volání <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> , <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> a <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> .  
  
 <xref:System.IO.Directory?displayProperty=nameWithType>Třídy a <xref:System.IO.File?displayProperty=nameWithType> poskytují statické metody pro načítání informací o adresářích a souborech.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, jak získat přístup k informacím o souborech a složkách.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Při zpracování řetězců cest zadaných uživatelem byste měli také zpracovat výjimky z následujících podmínek:  
  
- Název souboru je poškozený. Například obsahuje neplatné znaky nebo pouze mezery.  
  
- Název souboru má hodnotu null.  
  
- Název souboru je delší než maximální délka definovaná systémem.  
  
- Název souboru obsahuje dvojtečku (:).  
  
 Pokud aplikace nemá dostatečná oprávnění ke čtení zadaného souboru, `Exists` vrátí metoda `false` bez ohledu na to, zda cesta existuje. metoda nevyvolá výjimku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO?displayProperty=nameWithType>
- [Průvodce programováním v C#](../index.md)
- [Systém souborů a registr (Průvodce programováním v C#)](./index.md)
