---
title: "Vstupní znakovou sadu (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 691f29a04b1b1f997be501330ec887d6815d7531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="input-character-set-entity-sql"></a>Vstupní znakovou sadu (entita SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]přijme kódovaný v UTF-16 znaků UNICODE.  
  
 Textové literály může obsahovat libovolný znak UTF-16 uzavřená do jednoduchých uvozovek. Například N '文字列リテラル'. Při porovnání textové literály, použijí se původní hodnoty UTF-16. Například N'ABC, se liší v japonské a Latin kódové stránky.  
  
 Komentáře mohou obsahovat libovolný znak UTF-16.  
  
 Identifikátory uvozené řídicími znaky může obsahovat libovolný znak UTF-16 uzavřeny do hranatých závorek. Například [エスケープされた識別子]. Porovnání identifikátory uvozené UTF-16 nejsou rozlišována malá a velká písmena. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zpracovává verzích písmena, která zobrazí stejné, ale jsou z jiné znakové stránky jako jiné znaky. Například je ekvivalentní [abc] [ABC], pokud odpovídající znaky ze stejné znaková stránka. Pokud stejný dva identifikátory z jiné znakové stránky, jsou to ale není ekvivalentní.  
  
 Prázdné místo je libovolný znak prázdné znaky znakové sady UTF-16.  
  
 Nový řádek je všechny normalizovaný znak nového řádku UTF-16. Například '\n' a '\r\n, jsou považovány za znaky nového řádku, ale '\r' není znak nového řádku.  
  
 Klíčová slova, výrazy a interpunkční znaménka, může být libovolný znak UTF-16, který normalizuje k Latin. Například vyberte v japonské znaková stránka je platný – klíčové slovo.  
  
 Klíčová slova, výrazy a interpunkce lze pouze znaky latinky. `SELECT`v japonské kódová stránka není klíčové slovo. +,-, *, /, =, (,), ", [,] a dalších jazyk konstrukce není v uvozovkách zde lze pouze znaky latinky.  
  
 Jednoduché identifikátory lze pouze znaky latinky. Tím je zabráněno nejednoznačnosti při porovnávání, protože se pak porovnávají původní hodnoty. Například by být ABC liší v japonské a Latin kódové stránky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
