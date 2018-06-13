---
title: Uživatelem definované typy CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 344245ea7c67d7b5363c17bb42e2606ca11142bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357579"
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
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
