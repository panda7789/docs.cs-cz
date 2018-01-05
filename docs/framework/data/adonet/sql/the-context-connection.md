---
title: "Připojení kontextu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3bb732644bf9373d847eb14b63e69a756cb3ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="the-context-connection"></a>Připojení kontextu
Problém interních datových přístupu je docela běžný scénář. To znamená, že chcete na stejný server, na kterém common language runtime (CLR) uložené procedury nebo funkce provádí přistupuje. Jednou z možností je vytvořit připojení pomocí <xref:System.Data.SqlClient.SqlConnection>, zadejte připojovací řetězec, který odkazuje na místním serveru a otevřete připojení. To vyžaduje zadání pověření pro přihlášení. Připojení je v relaci k jiné databázi, než se uložená procedura nebo funkce, může mít různé `SET` možnosti, je v oddělené transakci, nezná dočasných tabulek, a tak dále. Pokud vaše spravované uložené procedury nebo funkce kód je prováděna v procesu systému SQL Server, je to, protože někdo připojený k tomuto serveru a příkaz SQL pro vyvolání ho. Budete ho zřejmě chtít uložená procedura nebo funkce, která má být spuštěn v kontextu tohoto připojení, spolu s jeho transakce `SET` možnosti a tak dále. Tomu se říká připojení kontextu.  
  
 Připojení kontextu umožňuje spustit příkazy jazyka Transact-SQL ve stejné oblasti, aby váš kód byl vyvolán na prvním místě. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1.  [Kontextové připojení](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
