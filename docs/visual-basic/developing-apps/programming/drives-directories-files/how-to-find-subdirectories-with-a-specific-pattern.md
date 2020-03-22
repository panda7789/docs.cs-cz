---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348771"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> vrátí kolekci řetězců jen pro čtení představující názvy cest pro podadresáře v adresáři. `wildCards` Parametr můžete použít k určení určitého vzoru. Pokud chcete do hledání zahrnout obsah podadresářů, nastavte `searchType` parametr `SearchOption.SearchAllSubDirectories`na .

Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné adresáře odpovídající zadanému vzoru.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Vyhledání podadresářů s určitým vzorem

Použijte `GetDirectories` metodu, která poskytuje název a cestu adresáře, který chcete prohledat. Následující příklad vrátí všechny adresáře ve struktuře adresářů, které obsahují slovo "Protokoly" v jejich názvu a přidá je do `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).

- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).

- Jeden nebo více zadaných zástupných znaků je `Nothing`prázdný řetězec<xref:System.ArgumentNullException>nebo obsahuje pouze mezery ( ).

- `directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).

- `directory`odkazuje na existující<xref:System.IO.IOException>soubor ( ).

- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).

- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).

- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).

- Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
