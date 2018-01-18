---
title: "Identity – objekt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21b8dbb934b778d792ff55d54f60fca92cac8e88
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="object-identity"></a>Identity – objekt
Objekty v modulu runtime mají jedinečné identity. Dvě proměnné, které odkazují na stejný objekt ve skutečnosti odkazovat na stejnou instanci objektu. Z tohoto důvodu jsou okamžitě viditelné prostřednictvím dalších změny provedené mimo jiné cestě prostřednictvím jednu proměnnou.  
  
 Řádky v tabulce relační databáze nemají jedinečných identit. Každý řádek obsahuje jedinečný primární klíč, a proto žádné dva řádky sdílet stejnou hodnotu klíče. Tento fakt však omezí pouze obsah databázové tabulky.  
  
 Ve skutečnosti se nejčastěji používá přenesou data z databáze a do jiné vrstvě, které aplikace pracuje s ním. Jedná se o model, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje. Když se přenesou data z databáze nástroje jako řádky, máte žádné očekává, že dva řádky, které představují stejná data ve skutečnosti odpovídají na stejný řádek instance. Pokud je dotaz pro konkrétního zákazníka dvakrát, zobrazí dva řádky dat. Každý řádek obsahuje stejné informace.  
  
 S objekty předpokládáte něco příliš neliší. Očekáváte, pokud požádáte <xref:System.Data.Linq.DataContext> stejné informace opakovaně, je ve skutečnosti získáte na stejnou instanci objektu. Toto chování se očekává, protože objekty mají zvláštní význam pro vaše aplikace a očekáváte, se bude chovat, jako jsou objekty. Je určený jako hierarchie nebo grafy. Očekáváte jako takový je načíst a nechcete dostávat multitudes replikovaných instancí právě, protože se zobrazí výzva pro samé více než jednou.  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.DataContext> spravuje identity objektu. Vždy, když je nový řádek načíst z databáze, řádek je zaznamenána v tabulce identity na základě klíče. primární a se vytvoří nový objekt. Vždy, když je načíst tento stejný řádek, je původní instance objektu předávány zpět do aplikace. Tímto způsobem <xref:System.Data.Linq.DataContext> překládá koncept identity jak je vidět v databázi (tj. primárních klíčů) do koncept identity pohledu jazyk (instance). Aplikace se zobrazují pouze objekt ve stavu, že nejprve byla načtena. Nová data, pokud se liší, budou zahozeny. Další informace najdete v tématu [načítání objektů z mezipaměti Identity](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Tento postup se používá ke správě integritu místní objekty za účelem podpory optimistickou metodu aktualizace. Protože pouze změny, které se provádějí až po objekt, je nejprve vytvořen jsou provedeny v aplikaci, je záměr aplikace zrušte. Pokud mezitím došlo změnám mimo strana, jsou identifikovány v době `SubmitChanges()` je volána.  
  
> [!NOTE]
>  Pokud se objekt požadoval dotaz snadno identifikovat jako jeden již načten, se spustí žádný dotaz. V tabulce identity funguje jako mezipaměť všech dříve načíst objekty.  
  
## <a name="examples"></a>Příklady  
  
### <a name="object-caching-example-1"></a>Objekt ukládání do mezipaměti Příklad 1  
 V tomto příkladu Pokud provést stejný dotaz dvakrát, zobrazí se odkaz na stejný objekt v paměti pokaždé, když.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Objekt ukládání do mezipaměti příklad 2  
 V tomto příkladu Pokud provést různé dotazy, které vracejí na stejném řádku z databáze, zobrazí se odkaz na stejný objekt v paměti pokaždé, když.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
