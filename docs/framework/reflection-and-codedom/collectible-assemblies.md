---
title: Kolekční sestavení pro generování dynamických typů
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b26da264b2da40e19db4bc5e3b3575505f5c979c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637739"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Kolekční sestavení pro generování dynamických typů

*Kolekční sestavení* jsou dynamické sestavení, které může být uvolněno bez uvolnění domény aplikace, ve kterém byly vytvořeny. Všechny spravované a nespravované paměti používané na kolekční sestavení a typy, které obsahuje, se nedá uvolnit. Informace, jako je název sestavení je odebrán z interních tabulkách.

Chcete-li povolit uvolnění, použijte <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> příznak při vytváření dynamických sestavení. Sestavení je přechodná (to znamená, ho nejdou ukládat) a je náchylné ke omezení popsaná v [omezení na Kolekční sestavení](#restrictions-on-collectible-assemblies) oddílu. Modul CLR (CLR) na kolekční sestavení uvolní automaticky při uvolnění všechny objekty přidružené k sestavení. Ve všech dalších ohledech jsou kolekční sestavení vytvořen a použít stejným způsobem jako ostatní dynamických sestavení.

## <a name="lifetime-of-collectible-assemblies"></a>Doba života kolekční sestavení

Existence odkazy na typy, které obsahuje a objekty, které jsou vytvářené z typů řídí životnost kolekční sestavení. Modul common language runtime neuvolní sestavení, tak dlouho, dokud jeden nebo více z následujících existují (`T` je libovolný typ, který je definovaný v sestavení): 

- Instance `T`.

- Instance pole `T`.
 
- Instance obecného typu, který má `T` jako jeden z argumentů typu. Jedná se o obecných kolekcí `T`i v případě, že kolekce je prázdná.

- Instance <xref:System.Type> nebo <xref:System.Reflection.Emit.TypeBuilder> , která představuje `T`. 

   > [!IMPORTANT]
   > Je nutné uvolnit všechny objekty, které představují části sestavení. <xref:System.Reflection.Emit.ModuleBuilder> , Který definuje `T` uchovává odkaz na <xref:System.Reflection.Emit.TypeBuilder>a <xref:System.Reflection.Emit.AssemblyBuilder> uchovává odkaz na objekt <xref:System.Reflection.Emit.ModuleBuilder>, takže se odkazy na tyto objekty musí být uvolněny. Dokonce i existenci <xref:System.Reflection.Emit.LocalBuilder> nebo <xref:System.Reflection.Emit.ILGenerator> používají v konstrukci `T` znemožňuje uvolnění.

- Statický odkaz na `T` jiným typem dynamicky definované `T1` , který je stále dostupný spuštěním kódu. Například `T1` může být odvozen od `T`, nebo `T` může být typ parametru metody `T1`.
 
- A **ByRef** do statických polí, která patří do `T`.

- A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, nebo <xref:System.RuntimeMethodHandle> , který odkazuje na `T` nebo na jednu ze součástí `T`.

- Instance libovolného objektu reflexe, která se dá použít nepřímo nebo přímo k přístupu <xref:System.Type> objekt, který reprezentuje `T`. Například <xref:System.Type> objekt pro `T` lze získat z typu pole, jehož typ prvku je `T`, nebo z obecného typu, který má `T` jako argument typu. 

- Metoda `M` v zásobníku volání jakékoli vlákno, kde `M` je metoda `T` nebo úrovni modulu metodu, která je definována v sestavení.

- Delegát pro statickou metodu, která je definována v modulu sestavení.

Pokud pouze jednu položku z tohoto seznamu existuje pouze jeden typ nebo jednu metodu v sestavení, modul runtime nemůže uvolnit sestavení.

> [!NOTE]
> Modul runtime neuvolní skutečně sestavení dokud spuštění finalizační metody pro všechny položky v seznamu.

Pro účely sledování životnosti Konstruovaný obecný typ, jako `List<int>` (v C#) nebo `List(Of Integer)` (v jazyce Visual Basic), která je vytvořená a používaných pro generování kolekční sestavení se považuje za byly definované v sestavení který obsahuje definici obecného typu nebo v sestavení, který obsahuje definici jednoho z argumentů typu. Přesné sestavení, který se používá je podrobnosti implementace a mohou se změnit.
 
## <a name="restrictions-on-collectible-assemblies"></a>Omezení na kolekční sestavení

Na kolekční sestavení se vztahují následující omezení: 

- **Statických odkazů.**   
  Typy v běžné dynamické sestavení nemůže mít statické odkazy na typy, které jsou definovány v kolekční sestavení. Například pokud definujete běžný typ, který je odvozen z typu v kolekční sestavení <xref:System.NotSupportedException> je vyvolána výjimka. Typ v kolekční sestavení může mít statické odkazy na typ v jiném kolekční sestavení, ale tato zásada rozšiřuje životnost odkazované sestavení k době života odkazující sestavení.

- **Komunikace s objekty COM**   
   Kolekční sestavení lze definovat rozhraní COM. rozhraní a žádné instance typů v rámci na kolekční sestavení lze převést na objekty modelu COM. Typ v kolekční sestavení nemůže sloužit jako obálka volatelná aplikacemi COM (CCW) nebo Obálka volatelná za běhu (RCW). Typy v kolekční sestavení však můžete použít objekty, které implementují rozhraní modelu COM.

- **Vyvolání platformy**   
   Metody, které mají <xref:System.Runtime.InteropServices.DllImportAttribute> atribut nebude kompilovat, pokud jsou deklarovány v kolekční sestavení. <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> Instrukci nelze použít v implementaci typu v kolekční sestavení a takové typy nelze zařadit do nespravovaného kódu. Můžete však volání do nativního kódu s využitím vstupní bod, který je deklarován v nekolekční sestavení.
 
- **zařazování**   
   Objekty (v konkrétní, delegátů), které jsou definovány v kolekční sestavení nelze zařadit. Toto je omezení na všechny přechodné emitovaný typy.

- **Načítání sestavení**   
   Emitování reflexe je pouze mechanismus, který je podporován pro načítání kolekční sestavení. Sestavení, která jsou načtena pomocí jakoukoli jinou formu načítání sestavení nemůže být uvolněna.
 
- **Objekty vázané na kontext**    
   Statické místní proměnné nejsou podporovány. Typy v kolekční sestavení nelze rozšířit <xref:System.ContextBoundObject>. Kód v kolekční sestavení však můžete použít objekty vázané na kontext, které jsou definovány jinde.

- **Data vlákna**       
   Vlákno statické proměnné nejsou podporovány.

## <a name="see-also"></a>Viz také:

- [Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
