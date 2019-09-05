---
title: Vstupní znaková sada (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
ms.openlocfilehash: b1c6475704ec384800af0b678edd943246bf8044
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250643"
---
# <a name="input-character-set-entity-sql"></a>Vstupní znaková sada (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]přijímá znaky UNICODE kódované v UTF-16.  
  
 Řetězcové literály můžou obsahovat libovolný znak UTF-16 uzavřený v jednoduchých uvozovkách. Například N ' 文字列リテラル '. Když jsou porovnávány řetězcové literály, jsou použity původní hodnoty UTF-16. Například N'ABC ' se liší v japonštině a znakových znakech latinky.  
  
 Komentáře mohou obsahovat libovolný znak UTF-16.  
  
 Řídicí identifikátory můžou obsahovat libovolný znak UTF-16 uzavřený v hranatých závorkách. Například [エスケープされた識別子]. Porovnání identifikátorů Escape ve formátu UTF-16 rozlišuje velká a malá písmena. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zpracovává verze písmen, které vypadají stejně, ale z různých znakových stránek jako jiné znaky. Například [ABC] je ekvivalentem [abc], pokud jsou odpovídající znaky ze stejné znakové stránky. Pokud jsou však stejné dva identifikátory z různých znakových stránek, nejsou ekvivalentní.  
  
 Prázdné místo je libovolný prázdný znak UTF-16.  
  
 Nový řádek je libovolný normalizovaný znak nového řádku UTF-16. Například "\n" a "\r\n" se považují za znaky nového řádku, ale "\r" není znak nového řádku.  
  
 Klíčová slova, výrazy a interpunkční znaménka můžou obsahovat libovolný znak UTF-16, který se normalizuje na latinku. Například vyberte v japonské znakové stránce platné klíčové slovo.  
  
 Klíčová slova, výrazy a interpunkční znaménka můžou být jenom Latinská písmena. `SELECT`v japonské znakové stránce není klíčové slovo. +,-, \*,/, =, (,), ', [,] a jakékoli jiné jazykové konstrukce, které nejsou uvedené v uvozovkách, můžou být jenom latinkou.  
  
 Jednoduché identifikátory můžou být jenom Latinská písmena. Tím se vyhnete nejednoznačnosti během porovnání, protože se porovnávají původní hodnoty. Například ABC by se lišilo v japonštině a znakových znakech latinky.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
