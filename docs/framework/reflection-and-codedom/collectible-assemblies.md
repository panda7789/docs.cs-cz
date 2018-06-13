---
title: Collectible sestavení pro generování dynamickém typu
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04a04e422fec14055d8ac3f50b9f2f18658a0f9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398256"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Collectible sestavení pro generování dynamickém typu

*Collectible sestavení* jsou dynamická sestavení, které mohou být odpojen bez uvolnění domény aplikace, v jakém byly vytvořeny. Se nedá uvolnit všechny spravovanými a nespravovanými paměti používané collectible sestavení a typy, které obsahuje. Informace, jako je název sestavení je odebrán z vnitřní tabulky.

Pokud chcete povolit uvolnění, použijte <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> příznak při vytváření dynamických sestavení. Sestavení je přechodný (to znamená, nelze ji uložit) a mohou podléhat omezení popsaná v [omezení Collectible sestavení](#restrictions-on-collectible-assemblies) části. Modul CLR (CLR) collectible sestavení uvolní automaticky při vydání všechny objekty přidružené sestavení. V ostatních ohledech jsou collectible sestavení vytvořit a použít stejným způsobem jako ostatní dynamická sestavení.

## <a name="lifetime-of-collectible-assemblies"></a>Doba platnosti collectible sestavení

Existují odkazy na typy, které obsahuje i s objekty, které jsou vytvořené z těchto typů řídí životnost collectible sestavení. Modul common language runtime neuvolní sestavení tak dlouho, dokud jeden nebo více z následujících existují (`T` je žádný typ, který je definovaný v sestavení): 

- Instance `T`.

- Instance pole `T`.
 
- Instance obecného typu, který má `T` jako jeden z jeho argumenty typu. To zahrnuje obecné kolekce `T`i v případě, že kolekce je prázdná.

- Instance <xref:System.Type> nebo <xref:System.Reflection.Emit.TypeBuilder> představující `T`. 

   > [!IMPORTANT]
   > Je nutné uvolnit všechny objekty, které představují části sestavení. <xref:System.Reflection.Emit.ModuleBuilder> , Který definuje `T` udržuje odkaz na <xref:System.Reflection.Emit.TypeBuilder>a <xref:System.Reflection.Emit.AssemblyBuilder> udržuje odkaz na objekt <xref:System.Reflection.Emit.ModuleBuilder>, takže odkazy na tyto objekty musí být vydání. I existenci <xref:System.Reflection.Emit.LocalBuilder> nebo <xref:System.Reflection.Emit.ILGenerator> použít pro výpočet `T` brání uvolnění.

- Statický odkaz na `T` jiným typem dynamicky definované `T1` spuštěním kódu se stále dostupný. Například `T1` může být odvozen z `T`, nebo `T` může být typ parametru v metoda `T1`.
 
- A **ByRef** do statických polí, která patří do `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, nebo <xref:System.RuntimeMethodHandle> který odkazuje na `T` nebo součást `T`.

- Instance reflexe objektu, který by bylo možné použít nepřímo nebo přímo k přístupu <xref:System.Type> objekt, který reprezentuje `T`. Například <xref:System.Type> objekt pro `T` lze získat z typu pole s typem elementu `T`, nebo z obecného typu, který má `T` jako argument typu. 

- Metoda `M` v zásobníku volání z libovolného vlákna, kde `M` je metoda `T` nebo úroveň modulu metodu, která je definována v sestavení.

- Delegát pro statickou metodu, která je definována v modulu sestavení.

Pokud jen jednu položku ze seznamu existuje pouze jeden typ nebo jednu metodu v sestavení, modul runtime nelze odinstalovat, sestavení.

> [!NOTE]
> Modul runtime neuvolní ve skutečnosti sestavení dokud spustili finalizační metody pro všechny položky v seznamu.

Pro účely sledování životnosti sestavené Obecné zadejte například `List<int>` (v jazyku C#) nebo `List(Of Integer)` (v jazyce Visual Basic), který je vytvořen a použít v generování collectible sestavení se považuje za byly definované v sestavení, obsahuje obecná definice typu nebo v sestavení, který obsahuje definici jednoho z jeho argumenty typu. Přesný sestavení, které se používá je podrobnosti implementace a která se může změnit.
 
## <a name="restrictions-on-collectible-assemblies"></a>Omezení collectible sestavení

Na collectible sestavení se vztahují následující omezení: 

- **Statické odkazy**   
  Typy v sestavení obyčejnou dynamické nemůže mít statické odkazy na typy, které jsou definovány v collectible sestavení. Pokud definujete obyčejnou typ, který dědí z typu v collectible sestavení, například <xref:System.NotSupportedException> je vyvolána výjimka. K typu v collectible sestavení může mít statické odkazy na typ v jiném collectible sestavení, ale tato zásada rozšiřuje životnost odkazované sestavení do životnost odkazující sestavení.

- **Zprostředkovatel komunikace s objekty COM**   
   V rámci collectible sestavení může být definováno žádné COM – rozhraní a žádné instance typů v rámci collectible sestavení mohou být převedeny na objekty modelu COM. K typu v collectible sestavení nemůže sloužit jako obálka volatelná aplikacemi COM (doleva) nebo Obálka volatelná za běhu (RCW). Typy v sestavení collectible však můžete použít objekty, které implementují rozhraní modelu COM.

- **Vyvolání platformy**   
   Metody, které mají <xref:System.Runtime.InteropServices.DllImportAttribute> atribut nebude kompilovat, když jsou deklarovány v collectible sestavení. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Instrukce nelze použít k implementaci určitého typu ve collectible sestavení a tyto typy nelze zařadit do nespravovaného kódu. Můžete však volání do nativního kódu s použitím vstupní bod, který je deklarován v jiných collectible sestavení.
 
- **Zařazování**   
   Objekty (ve konkrétní, delegáti), které jsou definovány v sestaveních collectible nelze zařadit. Toto je omezení na všech typech přechodný emitovaného.

- **Načítání sestavení**   
   Emitování reflexe pouze mechanismus, který je podporován pro načtení collectible sestavení. Sestavení, která jsou načtena pomocí jakoukoli jinou formu načítání sestavení nelze odpojit.
 
- **Kontext vazby objektů**    
   Kontext statické proměnné nejsou podporovány. Typy v sestavení collectible nelze rozšířit <xref:System.ContextBoundObject>. Kód v collectible sestavení však můžete použít objekty kontext vazby, které jsou definovány jinde.

- **Data statické přístup z více vláken**       
   Vlákno statické proměnné nejsou podporovány.

## <a name="see-also"></a>Viz také

[Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
