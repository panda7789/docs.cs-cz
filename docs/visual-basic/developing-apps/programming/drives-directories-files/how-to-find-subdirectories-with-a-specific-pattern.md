---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: c8e13598080139cafabffb2e17d0a3b99c37dc5d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348771"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro podadresáře v adresáři. K určení konkrétního vzoru můžete použít parametr `wildCards`. Chcete-li do hledání zahrnout obsah podadresářů, nastavte parametr `searchType` na hodnotu `SearchOption.SearchAllSubDirectories`.

Pokud se nenajde žádné adresáře vyhovující zadanému vzoru, vrátí se prázdná kolekce.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Vyhledání podadresářů s určitým vzorem

Použijte metodu `GetDirectories`, zadejte název a cestu k adresáři, který chcete vyhledat. Následující příklad vrátí všechny adresáře ve struktuře adresáře, které obsahují slovo "logs" v názvu, a přidá je do `ListBox1`.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).

- Jedna nebo více zadaných zástupných znaků je `Nothing`, prázdný řetězec nebo obsahuje pouze mezery (<xref:System.ArgumentNullException>).

- `directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).

- `directory` odkazuje na existující soubor (<xref:System.IO.IOException>).

- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).

- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).

- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).

- Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
