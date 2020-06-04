---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401625"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro podadresáře v adresáři. `wildCards`K určení konkrétního vzoru můžete použít parametr. Chcete-li do hledání zahrnout obsah podadresářů, nastavte `searchType` parametr na `SearchOption.SearchAllSubDirectories` .

Pokud se nenajde žádné adresáře vyhovující zadanému vzoru, vrátí se prázdná kolekce.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Vyhledání podadresářů s určitým vzorem

Použijte `GetDirectories` metodu, zadejte název a cestu adresáře, který chcete vyhledat. Následující příklad vrátí všechny adresáře ve struktuře adresáře, které obsahují slovo "logs" v názvu a přidá je do `ListBox1` .

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:

- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).

- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).

- Jeden nebo více zadaných zástupných znaků je `Nothing` , prázdný řetězec nebo obsahuje pouze mezery ( <xref:System.ArgumentNullException> ).

- `directory`neexistuje ( <xref:System.IO.DirectoryNotFoundException> ).

- `directory`odkazuje na existující soubor ( <xref:System.IO.IOException> ).

- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .

- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).

- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).

- Uživatel nemá potřebná oprávnění ( <xref:System.UnauthorizedAccessException> ).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Postupy: Hledání souborů pomocí specifického vzoru](how-to-find-files-with-a-specific-pattern.md)
