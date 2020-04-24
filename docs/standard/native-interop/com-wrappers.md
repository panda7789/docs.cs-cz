---
title: Obálky COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
ms.openlocfilehash: d647a8cd73fa714e86454687a25501259f894f6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120715"
---
# <a name="com-wrappers"></a>Obálky COM
Model COM se liší od modelu objektu .NET runtime v několika důležitých způsobech:  
  
- Klienti objektů COM musí spravovat životnost těchto objektů; modul CLR (Common Language Runtime) spravuje životnost objektů ve svém prostředí.  
  
- Klienti objektů COM zjišťují, zda je služba k dispozici, vyžádáním rozhraní, které poskytuje tuto službu a návratovým ukazatelem rozhraní. Klienti objektů .NET mohou získat popis funkcionality objektu pomocí reflexe.  
  
- Objekty sítě se nacházejí v paměti spravované spouštěcím prostředím modulu runtime .NET. Spouštěcí prostředí může přesunout objekty z paměti z důvodů výkonu a aktualizovat všechny odkazy na objekty, které přesouvá. Nespravované klienty, kteří získali ukazatel na objekt, spoléhají na to, že objekt zůstane ve stejném umístění. Tito klienti nemají žádný mechanismus pro práci s objektem, jehož umístění není opraveno.  
  
 Aby bylo možné tyto rozdíly překonat, modul runtime poskytuje obálkové třídy, aby spravované i nespravované klienty považovat za volání objektů v jejich příslušném prostředí. Pokaždé, když váš spravovaný klient volá metodu na objekt modelu COM, modul runtime vytvoří obálku s voláním [za běhu](runtime-callable-wrapper.md) (RCW). RCW abstrakce rozdílů mezi spravovanými a nespravovanými referenčními mechanismy mimo jiné. Modul runtime také vytvoří obálku s voláním [modelu COM](com-callable-wrapper.md) (doleva), aby mohl vrátit proces a povolit klientovi modelu COM bezproblémové volání metody objektu .NET. Jak ukazuje následující obrázek, perspektiva volajícího kódu určuje, která Obálková Třída modul runtime vytvoří.  
  
 ![Přehled obálky COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 Ve většině případů standardní RCW nebo doleva generované modulem runtime poskytuje adekvátní zařazování pro volání, která překračují hranice mezi COM a .NET Runtime. Pomocí vlastních atributů můžete volitelně upravit způsob, jakým modul runtime představuje spravovaný a nespravovaný kód.  
  
## <a name="see-also"></a>Viz také

- [Pokročilá interoperabilita modelu COM v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Obálka volatelná za běhu](runtime-callable-wrapper.md)
- [Obálka volatelná aplikacemi COM](com-callable-wrapper.md)
- [Přizpůsobení standardních obálek v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Postupy: přizpůsobení obálek za běhu, které lze volat v .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))
