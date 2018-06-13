---
title: Přístup k vlastním atributům
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aafd1586068dcd7aaf4a72ef5454e3a2698ccd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397088"
---
# <a name="accessing-custom-attributes"></a>Přístup k vlastním atributům
Po atributy nejsou spojené s prvky programu, reflexe můžete použít k dotazování jejich existence a hodnoty. V rozhraní .NET Framework verze 1.0 a 1.1 vlastní atributy jsou zkoumány v kontextu spuštění. Poskytuje rozhraní .NET Framework verze 2.0 nový kontext načítání pouze pro reflexi kontext, který můžete použít k prozkoumání kód, který nelze načíst pro provedení.  
  
## <a name="the-reflection-only-context"></a>Kontext pouze pro reflexi  
 Kód načtený do kontextu pouze pro reflexi nelze provést. To znamená, že nelze vytvořit instance vlastních atributů, protože, které by vyžadovaly provedením jejich konstruktory. Pokud chcete načíst a zkontrolujte vlastní atributy v kontextu pouze pro reflexi, použijte <xref:System.Reflection.CustomAttributeData> třídy. Instance této třídy lze získat pomocí statické předáte příslušnému přetížení <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metoda. V tématu [postupy: načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Kontext spuštění  
 Metody reflexe hlavní atributů dotazu v kontextu spuštění <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> a <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Usnadnění vlastního atributu se kontroluje s ohledem na sestavení, ve které je připojen. Jde o ekvivalent kontrola, zda metoda typu v sestavení, ve které je připojen vlastních atributů může volat konstruktor vlastního atributu.  
  
 Metody, jako <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> zkontrolujte viditelnost a usnadnění argumentem typu. Pouze kód v sestavení, které obsahuje uživatelsky definovaný typ. můžete načíst vlastní atribut tento typ použití **GetCustomAttributes**.  
  
 Následující příklad jazyka C# je návrhový vzor typické vlastních atributů. Ilustruje modelu reflexe runtime vlastních atributů.  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 Pokud při pokusu o načtení vlastní atributy pro veřejné vlastní typ atributu je v modulu runtime <xref:System.ComponentModel.DescriptionAttribute> připojené k **GetLanguage** metoda, provede následující akce:  
  
1.  Modul runtime kontroluje, zda argument typu **DescriptionAttribute** k **Type.GetCustomAttributes**(typ *typu*) je veřejný a proto je viditelná a přístupné.  
  
2.  Modul runtime kontroluje, zda uživatelem definovaný typ **MyDescriptionAttribute** je odvozena z **DescriptionAttribute** viditelné a zda je dostupný v rámci **System.Web.DLL**sestavení, kde je připojen k metodě **GetLanguage**().  
  
3.  Modul runtime kontroluje, zda konstruktoru **MyDescriptionAttribute** viditelné a zda je dostupný v rámci **System.Web.DLL** sestavení.  
  
4.  Modul runtime volání konstruktoru **MyDescriptionAttribute** s parametry vlastních atributů a vrací nový objekt volajícímu.  
  
 Model reflexe vlastních atributů může úniku instancí uživatelem definované typy mimo sestavení, ve kterém je definovaný typ. Nijak se to neliší od členů v knihovně system runtime, které vracejí instancí uživatelem definované typy, jako například <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> vrací pole **RuntimeMethodInfo** objekty. Členy typu být neveřejní definujte v případě, že aby klienta z zjišťování informací o uživateli definované vlastního typu atributu.  
  
 Následující příklad ukazuje základní způsob použití reflexe získat přístup k vlastní atributy.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
