---
title: "Čísla s plovoucí desetinnou čárkou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3e8ac8b5a97c62bb173fba57ac8aeb26a1dad42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="floating-point-numbers"></a>Čísla s plovoucí desetinnou čárkou
Toto téma popisuje některé problémy, které vývojáři často dojde, když pracují s plovoucí desetinnou čárkou v [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Tyto problémy jsou způsobena tím, že počítače ukládat čísla s plovoucí desetinnou čárkou a nejsou specifické pro konkrétního poskytovatele, jako <xref:System.Data.SqlClient> nebo <xref:System.Data.OracleClient>.  
  
 Čísla s plovoucí desetinnou čárkou obvykle nemají přesnou binární reprezentace. Místo toho počítač ukládá přibližný počet. V různou dobu může být různý počet číslic binární používá k reprezentování číslo. Když plovoucí bodu číslo je převedeno z jednoho reprezentace na jiné reprezentace minimálně platných číslic toto číslo může mírně lišit. Převod obvykle dochází, pokud je číslo přetypování z jednoho typu k jinému typu. Variaci nastane, zda dochází k převodu v databázi, mezi typy, které představují hodnot v databázi, nebo mezi typy. Tyto změny čísla, která by byla logicky stejná pravděpodobně změny v jejich nejméně významným číslic, které způsobit mají různé hodnoty. Počet číslic přesnost počet může být větší nebo menší než očekávanou. Při naformátovaná jako řetězec, číslo nemusí zobrazovat očekávané hodnotě.  
  
 Chcete-li minimalizovat těchto důsledcích, měli byste použít nejbližší nalezena shoda mezi číselnými typy, které jsou pro vás k dispozici. Například, pokud pracujete s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], přesný číselná hodnota může změnit při převodu hodnoty Transact-SQL skutečné typu na hodnotu typu float. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], převod <xref:System.Single> k <xref:System.Double> může také způsobit neočekávané výsledky. V obou případech se strategii je dobré provést všechny hodnoty v aplikaci použijte stejné číselného typu. Můžete také použít typu decimal-přesnost nebo přetypovat na typ desetinné číslo-přesnost s plovoucí desetinnou čárkou, než začnete pracovat s nimi.  
  
 Chcete-li vyřešit problémy s porovnání rovnosti, zvažte kódování aplikace tak, aby se ignorují rozdíly v minimálně platných číslic. Například místo porovnávání zobrazíte, zda jsou si rovny dvou čísel, odečte jedno číslo z jiné číslo. V případě, že rozdíl je v rámci přijatelné okraji zaokrouhlení, můžete aplikaci zacházet čísla jako v případě, že jsou stejné.  
  
## <a name="see-also"></a>Viz také  
 [Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
