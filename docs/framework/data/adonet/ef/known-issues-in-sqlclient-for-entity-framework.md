---
title: Známé problémy v SqlClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 5c0b7c32e00a0cc90367a559a41f5a7ab59a33a4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251393"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Známé problémy v SqlClient pro Entity Framework
Tato část popisuje známé problémy týkající se .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Koncové mezery v řetězcových funkcích  
 SQL Server ignoruje koncové mezery v řetězcových hodnotách. Proto předání koncových mezer v řetězci může vést k nepředvídatelným výsledkům, dokonce i selháním.  
  
 Pokud je nutné mít v řetězci koncové mezery, měli byste zvážit připojení prázdného znaku na konci, takže SQL Server řetězec neořízne. Pokud nejsou koncové mezery požadovány, měly by být oříznuty předtím, než budou předány do kanálu dotazu.  
  
## <a name="right-function"></a>PRAVÁ funkce  
 Pokud je hodnota bez`null` hodnoty předána jako první argument a 0 se předává jako druhý argument do `RIGHT(nvarchar(max)`, 0`)` nebo `RIGHT(varchar(max)`0`)`, `NULL` hodnota se vrátí místo `empty` řetězce.  
  
## <a name="cross-and-outer-apply-operators"></a>Operátory použití mezi a VNĚJŠÍmi operátory  
 Operátory VZÁJEMNÉho a VNĚJŠÍho použití byly představeny v SQL Server 2005. V některých případech může kanál dotazů vytvořit příkaz jazyka Transact-SQL, který obsahuje operátory KŘÍŽového nebo VNĚJŠÍho použití. Vzhledem k tomu, že někteří poskytovatelé back-end, včetně verzí SQL Server starších než SQL Server 2005, tyto operátory nepodporují, takové dotazy nelze na těchto back-end poskytovateli spustit.  
  
 Níže jsou uvedeny některé typické scénáře, které by mohly vést k přítomnosti operátorů VZÁJEMNÉho použití nebo VNĚJŠÍho použití v dotazu na výstup:  
  
- Korelační poddotaz se stránkováním.  
  
- `AnyElement` Přes korelační poddotaz nebo přes kolekci vytvořenou navigací.  
  
- Dotazy LINQ používající seskupovací metody, které přijímají selektor elementu.  
  
- Explicitně se zadává dotaz, ve kterém se explicitně zařadí nebo nastaví vnější.  
  
- Dotaz, který má DEREF konstrukci nad konstrukcí REF.  
  
## <a name="skip-operator"></a>SKIP – operátor  
 Pokud používáte SQL Server 2000, může při použití příkazu přeskočit s řazením na jiné než klíčové sloupce vracet nesprávné výsledky. Pokud neklíčový sloupec obsahuje duplicitní data, může být vynecháno více než zadaný počet řádků. Je to kvůli tomu, jak je PŘESKOČENí přeloženo pro SQL Server 2000. Například v následujícím dotazu může být vynecháno více než pět řádků, pokud `E.NonKeyColumn` má duplicitní hodnoty:  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Cílení na správnou verzi SQL Server  
 Cílí na dotaz Transact-SQL na základě verze SQL Server, která je zadána `ProviderManifestToken` v atributu schématu elementu v souboru modelu úložiště (. ssdl). [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Tato verze se může lišit od verze samotného SQL Server, ke které jste se připojili. Například pokud používáte SQL Server 2005, ale `ProviderManifestToken` atribut je nastaven na 2008, vygenerovaný dotaz Transact-SQL se nemusí na serveru spustit. Například dotaz, který používá nové typy data a času, které byly představeny v SQL Server 2008, nebude proveden v dřívějších verzích SQL Server. Pokud používáte SQL Server 2005, ale váš `ProviderManifestToken` atribut je nastaven na 2000, vygenerovaný dotaz Transact-SQL může být méně optimalizovaný nebo se může zobrazit výjimka, která říká, že dotaz není podporován. Další informace najdete v části různé a vnější operátory použití výše v tomto tématu.  
  
 Určité chování databáze závisí na úrovni kompatibility nastavené na databázi. Pokud je `ProviderManifestToken` atribut nastavený na 2005 a vaše verze SQL Server je 2005, ale úroveň kompatibility databáze je nastavená na "80" (SQL Server 2000), vygenerovaná procedura Transact-SQL bude cílena na SQL Server 2005, ale nemusí se spouštět podle očekávání z důvodu nastavení úrovně kompatibility. Například může dojít ke ztrátě informací o řazení, pokud název sloupce v seznamu ORDER BY odpovídá názvu sloupce v selektoru.  
  
## <a name="nested-queries-in-projection"></a>Vnořené dotazy v projekci  
 Vnořené dotazy v klauzuli projekce můžou být přeložené do Kartézskémch dotazů na produkt na serveru. Na některých back-end serverech, včetně serveru SQL, to může způsobit, že tabulka TempDB bude velmi velká. To může snížit výkon serveru.  
  
 Následuje příklad vnořeného dotazu v klauzuli projekce:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Vygenerované hodnoty identity GUID serveru  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Podporuje hodnoty identity typu GUID generované serverem, ale poskytovatel musí po vložení řádku podporovat vrácení hodnoty identity vygenerované serverem. Počínaje SQL Server 2005 můžete vrátit typ GUID generovaný serverem v databázi SQL Server prostřednictvím [klauzule OUTPUT](https://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Viz také:

- [SqlClient pro Entity Framework](sqlclient-for-the-entity-framework.md)
- [Známé problémy a aspekty u LINQ to Entities](./language-reference/known-issues-and-considerations-in-linq-to-entities.md)
