---
title: Připojení kontextu
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 0d079eb1aa2fa7affa53d53ddd651948acd92383
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865046"
---
# <a name="the-context-connection"></a>Připojení kontextu
Problém interní datové je poměrně běžný scénář. To znamená, že budete chtít na stejný server, na kterém common language runtime (CLR) uložená procedura nebo funkce provádí přistupuje. Jednou z možností je vytvořit připojení pomocí <xref:System.Data.SqlClient.SqlConnection>, zadejte připojovací řetězec, který odkazuje na místním serveru a otevřete připojení. To vyžaduje, když zadáváte přihlašovací údaje pro přihlášení. Připojení je v relaci jiné databáze než uloženou proceduru nebo funkci, mohou mít různé `SET` možnosti, je v samostatných transakcích, nezobrazí dočasné tabulky, a tak dále. Pokud vaše spravované uložené procedury nebo funkce kódu je spouštěn v procesu serveru SQL Server, bude to, že někdo připojené k tomuto serveru a provedený SQL příkaz jej lze vyvolat. Budete zřejmě chtít uložená procedura nebo funkce pro spuštění v kontextu tohoto připojení, spolu s jeho transakce `SET` možnosti a tak dále. Tomu se říká připojení kontextu.  
  
 Připojení kontextu umožňuje spuštění příkazů jazyka Transact-SQL ve stejném kontextu, že váš kód byl spuštěn na prvním místě. Podrobnější informace najdete v tématu verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
1.  [Kontextové připojení](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření objektů serveru SQL Server 2005 ve spravovaném kódu](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
