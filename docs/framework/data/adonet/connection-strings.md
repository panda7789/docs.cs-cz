---
title: "Připojovací řetězce v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a20061c551f5cb1a19c64a2f92b8180465f58eb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="connection-strings-in-adonet"></a>Připojovací řetězce v technologii ADO.NET
Rozhraní .NET Framework 2.0 zavedl nové funkce pro práci s připojovací řetězce, včetně zavedení nových klíčových slov do Tvůrce třídy řetězec připojení, které usnadňují vytváření řetězců platné připojení v době běhu.  
  
 Připojovací řetězec obsahuje inicializace informace, které se předá jako parametr ze zprostředkovatele dat pro zdroj dat. Syntaxe závisí na poskytovateli dat a připojovací řetězec je analyzovat při pokusu o otevření připojení. Chyby syntaxe generování výjimek spuštění, ale jiné chyby dojít pouze po zdroj dat obdrží informace o připojení. Po ověření, zdroj dat použije možnosti zadaný v připojovacím řetězci a otevře připojení.  
  
 Formát připojovací řetězec je oddělený středníkem seznam párů klíč/hodnota parametru:  
  
 `keyword1=value; keyword2=value;`  
  
 Klíčová slova nejsou velká a malá písmena a mezery mezi páry klíč/hodnota jsou ignorovány. Hodnoty mohou být velká a malá písmena, v závislosti na zdroji dat. Všechny hodnoty obsahující středníkem, apostrofech nebo dvojité uvozovky musí být uzavřena v uvozovkách.  
  
 Platný připojovací řetězec syntaxe závisí na poskytovateli a vývoj v průběhu let z dřívějších rozhraní API jako ODBC událostí. Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) zahrnuje mnoho prvků z starší syntaxe a je obecně flexibilnější s běžné syntaxi připojovacího řetězce. Jsou často stejně platný synonyma pro elementy syntaxe připojovacího řetězce, ale některé syntaxe a pravopisné chyby může způsobit problémy. Například "`Integrated Security=true`" je platná, zatímco "`IntegratedSecurity=true`" dojde k chybě. Kromě toho připojovací řetězce s vytvořeným za běhu z neověřený vstup uživatele může vést k útokům vkládání řetězce, ohrožující zabezpečení ve zdroji dat.  
  
 K řešení těchto problémů, ADO.NET 2.0 zavedl nový Tvůrci řetězců pro připojení pro každého zprostředkovatele dat .NET Framework. Klíčová slova jsou zveřejněné jako vlastnosti, povolení syntaxi připojovacího řetězce k ověření před odesláním ke zdroji dat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Ukazuje, jak používat `ConnectionStringBuilder` třídy vytvořit platný připojovací řetězce na dobu běhu.  
  
 [Připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Demonstruje způsob ukládání a načítání připojovací řetězce v konfiguračních souborech.  
  
 [Syntaxe připojovacího řetězce](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Popisuje postup konfigurace specifický pro zprostředkovatele připojovací řetězce pro `SqlClient`, `OracleClient`, `OleDb`, a `Odbc`.  
  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Ukazuje techniky pro ochranu informace, které slouží k připojení ke zdroji dat.  
  
## <a name="see-also"></a>Viz také  
 [Připojení ke zdroji dat](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
