---
title: "Uživatelem definované typy CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7b083dd7284789b1d0271bc688c08bbae591e160
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-user-defined-types"></a>Uživatelem definované typy CLR
Microsoft SQL Server poskytuje podporu pro uživatelem definované typy (UDT) implementuje pomocí rozhraní Microsoft .NET Framework common language runtime (CLR). Modul CLR je integrován do systému SQL Server a tento mechanismus můžete rozšířit systém typů databáze. UDT zajistí možnosti rozšíření uživatele systém typů dat systému SQL Server, a také schopnost definovat strukturovaných komplexní typy.  
  
 UDT můžete zadat dvě klíčové výhody z hlediska architektury aplikaci.  
  
-   Silné zapouzdření (i v klientovi a serveru) mezi vnitřní stav a externí chování.  
  
-   Těsná integrace s jinými související s funkcí serveru. Jakmile definujete vlastní UDT, můžete ji ve všech kontextech kde můžete použít typ systému v systému SQL Server, včetně definice sloupců a jako proměnné, parametry, výsledky funkce, kurzory, aktivační události a replikace.  
  
 Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1.  [Uživatelem definované typy CLR](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
