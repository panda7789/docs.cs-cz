---
title: Řešení potíží se zprostředkovateli typů
description: 'Zjistěte potenciální řešení problémů, ke kterým máte pravděpodobně dojde při použití poskytovatelů typů v jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f3b8ffdaf615563305b7b84b45a9ed1e066d0dcc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45589125"
---
# <a name="troubleshooting-type-providers"></a>Řešení potíží se zprostředkovateli typů

Toto téma popisuje a obsahuje potenciální řešení problémů, které se pravděpodobně setkáte při použití poskytovatelů typů.

## <a name="possible-problems-with-type-providers"></a>Možné problémy s poskytovateli typů

Pokud dojde k potížím při práci s poskytovateli typů, najdete v následující tabulce pro běžná řešení.

|Problém|Doporučené akce|
|-------|-----------------|
|**Změny schématu**. Zadejte pracovní poskytovatelé nejlépe při schématu zdroje dat je stabilní. Pokud přidáte data tabulky nebo sloupce nebo provést změny tohoto schématu, zprostředkovatel typu automaticky nerozpozná tyto změny.|Čištění nebo opětovném sestavení projektu. Chcete-li vyčistit projekt, zvolte **sestavení**, **Vyčistit** *ProjectName* na řádku nabídek. Chcete-li znovu sestavit projekt, zvolte **sestavení**, **znovu sestavit** *ProjectName* na řádku nabídek. Tyto akce resetování všech stav poskytovatele typu a vynutit zprostředkovatele, který se znovu připojit ke zdroji dat a získat informace o aktualizace schématu.|
|**Chyba připojení**. Adresa URL nebo připojovací řetězec je nesprávná, sítě nebo zdroj dat nebo služba není k dispozici.|Pro webovou službu nebo služby OData můžete zkusit adresy URL v aplikaci Internet Explorer a ověřte, zda adresa URL je správná a služba není k dispozici. Pro připojovací řetězec databáze, můžete použít nástroje datového připojení v **Průzkumníka serveru** a ověřte, zda je platný připojovací řetězec a databáze je k dispozici. Po obnovení připojení by měl pak vyčistit nebo znovu sestavit projekt tak, aby se typ zprostředkovatele připojení k síti.|
|**Neplatné přihlašovací údaje**. Musíte mít platný oprávnění pro datové zdroje nebo webové služby.|Pro připojení SQL musí být platný pro databázi, uživatelské jméno a heslo, které jsou určené v připojovací řetězec nebo v konfiguračním souboru. Pokud používáte ověřování Windows, musíte mít přístup k databázi. Správce databáze můžete určit, co oprávnění, které potřebujete pro přístup ke každé databázi a každý prvek v databázi.<br /><br />Pro webovou službu nebo datové služby musí mít příslušná pověření. Většina poskytovatelů typů poskytují DataContext objektu, který obsahuje vlastnosti přihlašovacích údajů, kterou můžete nastavit příslušné uživatelské jméno a přístupový klíč.|
|**Není platná cesta**. Cesta k souboru není platný.|Ověřte, zda je cesta zadána správně a soubor existuje. Kromě toho vám musí správně nabídka jakékoli backlashes v cestě nebo použijte doslovný řetězec nebo řetězce uvozené třemi uvozovkami.|

## <a name="see-also"></a>Viz také:

- [Zprostředkovatelé typů](index.md)
