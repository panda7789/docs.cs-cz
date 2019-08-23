---
title: Práce s jazykem DDL (Data Description Language)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: c2812e261278af7763bc6b2e1a493b97cb35e3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911635"
---
# <a name="working-with-data-definition-language"></a>Práce s jazykem DDL (Data Description Language)
Počínaje verzí .NET Framework 4 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] podporuje jazyk DDL (Data Definition Language). To vám umožní vytvořit nebo odstranit instanci databáze založenou na připojovacím řetězci a metadatech modelu úložiště (SSDL).  
  
 Následující metody pro <xref:System.Data.Objects.ObjectContext> použití připojovacího řetězce a obsahu SSDL k provedení následujících akcí: vytvořit nebo odstranit databázi, ověřit, zda databáze existuje, a zobrazit generovaný skript DDL:  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> Spuštění příkazů DDL předpokládá dostatečná oprávnění.  
  
 Výše uvedené metody přenesly většinu práce na základního poskytovatele dat ADO.NET. Je zodpovědností poskytovatele, aby bylo zajištěno, že konvence vytváření názvů používané pro generování databázových objektů je konzistentní s konvencemi použitými pro dotazování a aktualizace.  
  
 Následující příklad ukazuje, jak vygenerovat databázi na základě existujícího modelu. Také přidá nový objekt entity do kontextu objektu a uloží jej do databáze.  
  
## <a name="procedures"></a>Procedury  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a>Definování databáze na základě existujícího modelu  
  
1. Vytvořte konzolovou aplikaci.  
  
2. Přidejte do své aplikace existující model.  
  
    1. Přidejte prázdný model s názvem `SchoolModel`. Chcete-li vytvořit prázdný model, přečtěte si téma [postupy: Vytvoří nový soubor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) . edmx.  
  
     Do projektu se přidá soubor SchoolModel. edmx.  
  
    1. Zkopírujte obsah koncepčního, úložiště a mapování pro školní model z tématu [školní model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .  
  
    2. Otevřete soubor SchoolModel. edmx a vložte obsah do `edmx:Runtime` značek.  
  
3. Do funkce Main přidejte následující kód. Kód inicializuje připojovací řetězec k vašemu databázovému serveru, zobrazí skript DDL, vytvoří databázi, přidá novou entitu do kontextu a uloží změny do databáze.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
