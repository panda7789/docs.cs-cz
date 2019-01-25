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
ms.openlocfilehash: fb537950ce240d77282551f847b637a77792a264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645233"
---
# <a name="accessing-custom-attributes"></a>Přístup k vlastním atributům
Po atributy byly spojeny s prvky programu, reflexe je možné zadávat dotazy na jejich existence a hodnoty. V rozhraní .NET Framework verze 1.0 a 1.1 uživatelských atributů, které jsou zkoumány podle kontextu spuštění. Rozhraní .NET Framework verze 2.0 obsahuje nový kontext načtení kontextu pouze pro reflexi, který slouží ke kontrole kódu, který nelze načíst pro spuštění.  
  
## <a name="the-reflection-only-context"></a>Kontextu pouze pro reflexi  
 Nelze spustit kód načtený do kontextu pouze pro reflexi. To znamená, že nelze vytvořit instance vlastních atributů, protože, které by vyžadovaly provádění jejich konstruktory. Chcete-li načíst a zkontrolovat vlastních atributů v kontextu pouze pro reflexi, použijte <xref:System.Reflection.CustomAttributeData> třídy. Instance této třídy lze získat pomocí odpovídající přetížení statické <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> metody. Zobrazit [jak: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Kontext spuštění  
 Metody reflexe hlavní atributy dotazu v kontextu spuštění jsou <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> a <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Usnadnění vlastního atributu je zaškrtnuté políčko s ohledem na sestavení, ve které je připojené. Jde o ekvivalent kontroluje, zda můžete volat metody pro typ v sestavení, ve kterém je vlastní atribut připojen konstruktoru vlastního atributu.  
  
 Metody jako <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> zkontrolujte viditelnost a přístupnost typu argumentu. Pouze pro kód v sestavení, který obsahuje uživatelem definovaný typ může načíst vlastní atribut pomocí tohoto typu **GetCustomAttributes**.  
  
 Následující C# příklad je vzor návrh typický vlastní atribut. Ilustruje modelu reflexe runtime vlastního atributu.  
  
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
  
 Pokud při pokusu o načtení vlastních atributů pro veřejné vlastní typ atributu je v modulu runtime <xref:System.ComponentModel.DescriptionAttribute> připojené k **getlanguage –** metoda, provede následující akce:  
  
1.  Modul runtime kontroluje, že argument typu **DescriptionAttribute** k **Type.GetCustomAttributes**(typ *typ*) je veřejná a proto je viditelný a přístupný.  
  
2.  Modul runtime kontroluje, zda uživatelský typ **MyDescriptionAttribute** , která je odvozena od **DescriptionAttribute** je viditelný a přístupný v rámci **System.Web.DLL**sestavení, ve kterém je připojen k metodě **getlanguage –**().  
  
3.  Modul runtime kontroluje, že konstruktor třídy **MyDescriptionAttribute** je viditelný a přístupný v rámci **System.Web.DLL** sestavení.  
  
4.  Modul runtime volá konstruktor třídy **MyDescriptionAttribute** s parametry, které vlastní atribut a vrátí nový objekt volajícímu.  
  
 Model reflexe vlastních atributů může způsobit únik těchto instance uživatelsky definované typy mimo sestavení, ve kterém je typ definován. To se nijak neliší od členů v knihovně modulu runtime systému, které vracejí výskyty uživatelem definované typy, jako například <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> vrací pole **RuntimeMethodInfo** objekty. Aby klient zjišťování informací o typu uživatelem definované vlastní atribut definujte členy tohoto typu bude neveřejné.  
  
 Následující příklad ukazuje základní způsob, jak získat přístup k vlastní atributy pomocí operace reflection.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
