---
title: Kolekční sestavení pro generování dynamických typů
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 02c7048e0321282463aa3558287d1d13c5e4f8d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180548"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Kolekční sestavení pro generování dynamických typů

*Sběratelská sestavení* jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byla vytvořena. Všechny spravované a nespravované paměti používané sběratelské sestavení a typy, které obsahuje lze rekultivovat. Informace, jako je název sestavení, jsou odebrány z vnitřních tabulek.

Chcete-li povolit <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> uvolnění, použijte příznak při vytváření dynamické sestavy. Sestava je přechodná (to znamená, že ji nelze uložit) a podléhá omezením popsaným v části [Omezení sběratelských sestavení.](#restrictions-on-collectible-assemblies) Běžný jazyk runtime (CLR) uvolní sběratelské sestavení automaticky při uvolnění všech objektů přidružených k sestavení. Ve všech ostatních ohledech jsou sběratelská sestavy vytvářena a používána stejným způsobem jako ostatní dynamické sestavy.

## <a name="lifetime-of-collectible-assemblies"></a>Životnost sběratelských sestav

Životnost sběratelské sestavení je řízena existencí odkazů na typy, které obsahuje, a objekty, které jsou vytvořeny z těchto typů. Běžný jazyk runtime neuvolní sestavení tak dlouho, dokud jeden`T` nebo více z následujících existují ( je libovolný typ, který je definován v sestavení):

- Instance `T`aplikace .

- Instance pole `T`.

- Instance obecného typu, `T` který má jako jeden z jeho argumentů typu. To zahrnuje obecné `T`kolekce , i v případě, že kolekce je prázdný.

- Instance <xref:System.Type> nebo <xref:System.Reflection.Emit.TypeBuilder> která `T`představuje .

   > [!IMPORTANT]
   > Je nutné uvolnit všechny objekty, které představují části sestavy. Definuje, <xref:System.Reflection.Emit.ModuleBuilder> který `T` definuje udržuje <xref:System.Reflection.Emit.TypeBuilder>odkaz na <xref:System.Reflection.Emit.AssemblyBuilder> , a objekt <xref:System.Reflection.Emit.ModuleBuilder>udržuje odkaz na , takže odkazy na tyto objekty musí být uvolněna. Dokonce i existence <xref:System.Reflection.Emit.LocalBuilder> nebo <xref:System.Reflection.Emit.ILGenerator> použité při `T` stavbě brání vykládce.

- Statický odkaz `T` na jiný dynamicky `T1` definovaný typ, který je stále dosažitelný spuštěním kódu. `T1` Může například odvodit `T`z , nebo `T` může být `T1`typ parametru v metodě .

- A **ByRef** na statické pole, které patří do `T`.

- A <xref:System.RuntimeTypeHandle> <xref:System.RuntimeFieldHandle>, <xref:System.RuntimeMethodHandle> nebo který `T` odkazuje na nebo `T`na složku .

- Instance jakékoli reflexe objektu, který by mohl <xref:System.Type> být použit `T`nepřímo nebo přímo pro přístup k objektu, který představuje . <xref:System.Type> Například objekt pro `T` lze získat z typu pole, `T`jehož typ prvku `T` je , nebo z obecného typu, který má jako argument typu.

- Metoda `M` v zásobníku volání libovolného `M` vlákna, `T` kde je metoda nebo metoda na úrovni modulu, která je definována v sestavení.

- Delegát na statickou metodu, která je definována v modulu sestavení.

Pokud existuje pouze jedna položka z tohoto seznamu pouze pro jeden typ nebo jednu metodu v sestavení, runtime nemůže uvolnit sestavení.

> [!NOTE]
> Runtime není ve skutečnosti uvolnit sestavení, dokud finalizační metody byly spuštěny pro všechny položky v seznamu.

Pro účely sledování životnosti je vytvořený `List<int>` obecný typ, například (v jazyce C#) nebo `List(Of Integer)` (v jazyce Visual Basic), který je vytvořen a používán při generování sběratelského sestavení, považován za definovaný buď v sestavení, které obsahuje definici obecného typu, nebo v sestavení, které obsahuje definici jednoho z jeho argumentů typu. Přesné sestavení, které se používá, je podrobnosti implementace a může změnit.

## <a name="restrictions-on-collectible-assemblies"></a>Omezení sběratelských sestav

Pro sběratelská sestavení platí následující omezení:

- **Statické odkazy** Typy v běžné dynamické sestavení nemůže mít statické odkazy na typy, které jsou definovány ve sběratelské sestavení. Například pokud definujete běžný typ, který dědí z typu <xref:System.NotSupportedException> ve sběratelském sestavení, je vyvolána výjimka. Typ ve sběratelské sestavě může mít statické odkazy na typ v jiné sběratelské sestavě, ale to prodlužuje životnost odkazovaného sestavení na životnost odkazující sestavy.

- **KOM interop** V rámci sběratelského sestavení nelze definovat žádná rozhraní modelu COM a žádné instance typů v rámci sběratelského sestavení nelze převést na objekty COM. Typ ve sběratelské sestavě nemůže sloužit jako com volatelné obálky (CCW) nebo runtime volatelné obálky (RCW). Typy ve sběratelských sestaveních však mohou používat objekty, které implementují rozhraní COM.

- **Vyvolání platformy** Metody, které <xref:System.Runtime.InteropServices.DllImportAttribute> mají atribut nebude kompilovat, pokud jsou deklarovány ve sběratelské sestavení. Instrukce <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> nelze použít při implementaci typu ve sběratelské sestavení a tyto typy nelze zařazovat do nespravovaného kódu. Můžete však volat do nativního kódu pomocí vstupního bodu, který je deklarován v nesběratelském sestavení.

- **Zařazování** Objekty (zejména delegáti), které jsou definovány ve sběratelských sestaveních, nelze zařadit. Toto je omezení pro všechny přechodné emitované typy.

- **Montážní zatížení** Odraz emituje je jediný mechanismus, který je podporován pro načítání sběratelských sestav. Sestavení, která jsou načtena pomocí jiné formy nakládky sestavy, nelze uvolnit.

- **Kontextové objekty** Kontextové statické proměnné nejsou podporovány. Typy ve sběratelské sestavě nelze rozšířit <xref:System.ContextBoundObject>. Kód ve sběratelských sestaveních však může používat kontextové objekty, které jsou definovány jinde.

- **Statická data z vlákna** Proměnné statické podprocesy nejsou podporovány.

## <a name="see-also"></a>Viz také

- [Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)
