---
title: "PŘEJDĚTE (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c82149fb5d76ac7b95198ce2b29550eade54b48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="navigate-entity-sql"></a>PŘEJDĚTE (entita SQL)
Přejde přes vztahu mezi entity.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a>Arguments  
 `instance-expresssion`  
 Instance entity.  
  
 `relationship-type`  
 Název typu vztahu z soubor konceptuálního schématu definition language (CSDL). `relationship-type` Je kvalifikovaný jako \<obor názvů >.\< Název typu vztahu >.  
  
 `to`  
 Konec relace.  
  
 `from`  
 Začátek relace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud na kardinalitu pro ukončení je 1, bude vrácenou hodnotu `Ref<T>`. Pokud na kardinalitu na konec n, bude vrácenou hodnotu `Collection<Ref<T>>`.  
  
## <a name="remarks"></a>Poznámky  
 První třídy konstrukce v se vztahy [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM). Vztahy lze navázat mezi dva nebo více typy entit a uživatelé mohou přejít přes vztah z jednoho elementu end (entita) do jiné. `from`a `to` jsou podmíněně volitelné při překladu názvů v rámci relace nedochází k nejednoznačnosti.  
  
 NAVIGOVAT je platná v prostoru O a C.  
  
 Obecná forma konstrukce navigace je následující:  
  
 přejděte (`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ]])  
  
 Příklad:  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 Kde je OrderCustomer `relationship`, a jsou zákazníka a pořadí `to-end` (zákazníka) a `from-end` (pořadí elementů) vztahu. Jestliže byl OrderCustomer relaci n: 1, bude výsledný typ výrazu přejděte Ref\<zákazníka >.  
  
 Jednodušší formu výrazu je následující:  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 Podobně v dotazu má následující formu, přejděte výraz byste mohli vytvořit kolekci < Ref\<pořadí >>.  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 Instance výraz musí být typu entity nebo ref.  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru přejděte přejděte přes vztahu mezi adresu a SalesOrderHeader typy entit. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Postupy: přejděte relace se přejděte – operátor](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
