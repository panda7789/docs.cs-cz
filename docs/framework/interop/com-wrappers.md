---
title: Obálky COM
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60f5acf6ed8a7fe0bb2e6293666c33a479d25643
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="com-wrappers"></a>Obálky COM
COM se liší od objektový model rozhraní .NET Framework důležité několika způsoby:  
  
-   Klienti COM – objekty musí spravovat dobu životnosti těchto objektů; modul common language runtime spravuje životnosti objektů ve svém prostředí.  
  
-   Klienti COM – objekty zjistit, zda je služba k dispozici vyžádáním rozhraní, které poskytuje služby a získávání zpět ukazatele rozhraní, nebo ne. Klienti objekty .NET můžete získat popis objektu funkcí pomocí reflexe.  
  
-   NET objekty jsou umístěny v paměti spravuje prostředí pro spuštění rozhraní .NET Framework. Spuštění prostředí můžete pohyb objektů v paměti z důvodů výkonu a aktualizujte všechny odkazy na objekty, které ji přesune. Nespravované klientů, které získaly ukazatel na objekt, spoléhají na objekt, který má zůstat ve stejném umístění. Tito klienti měli žádný mechanismus pro práci s objektem, jehož umístění není pevný.  
  
 K překonání tyto rozdíly, poskytuje modul runtime obálkové třídy, aby klienti spravovaných i nespravovaných vezměte v úvahu, že volají objektů v rámci příslušnému prostředí. Vždy, když spravovaného klienta volá metodu na objekt modelu COM, modul runtime vytvoří [obálka volatelná za běhu](runtime-callable-wrapper.md) (RCW). RCWs abstraktní rozdíly mezi spravovanými a nespravovanými odkaz mechanismy, mimo jiné. Modul runtime také vytvoří [obálka volatelná aplikacemi COM](com-callable-wrapper.md) (doleva), chcete-li se vrátit do, povolení klient COM bezproblémově volat metodu na objekt .NET. Jak ukazuje následující obrázek, určuje, které Obálková třída modul runtime vytvoří perspektivy volající kód.  
  
 ![Přehled obálky COM](media/bidirectional.gif "obousměrného")  
Přehled obálky COM  
  
 Ve většině případů poskytuje standardní RCW nebo doleva generované modulem runtime odpovídající zařazování pro volání, které překračují hranice mezi COM a .NET Framework. Pomocí vlastních atributů, můžete volitelně upravit způsob, jakým modul runtime představuje spravovanými a nespravovanými kódu.  
  
## <a name="see-also"></a>Viz také  
 [Interoperabilita modelů COM Upřesnit](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb(v=vs.100))  
 [Obálka volatelná za běhu](runtime-callable-wrapper.md)  
 [Obálka volatelná aplikacemi COM](com-callable-wrapper.md)  
 [Přizpůsobení standardních obálek](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))  
 [Postupy: přizpůsobení běhové obálky s možností](https://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732(v=vs.100))
