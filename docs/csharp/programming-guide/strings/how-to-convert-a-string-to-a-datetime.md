---
title: "Postupy: Převedení řetězce na typ DateTime (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b459f245f0090fff16918bceb12a0082f6944331
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a>Postupy: Převedení řetězce na typ DateTime (Průvodce programováním v C#)
Je běžné pro programy, chcete-li povolit uživatelům zadat kalendářních dat jako řetězce hodnoty. Převést data na základě řetězců <xref:System.DateTime?displayProperty=nameWithType> objekt, můžete použít <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> metoda nebo <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> statickou metodu, jak je znázorněno v následujícím příkladu.  
  
 **Jazyková verze**.  Různé jazykové verze na světě zapisovat data řetězce různými způsoby.  Například v USA 01/20/2008 je 20. ledna 2008.  V Francie to vyvolá výjimku InvalidFormatException. Je to proto, že Francie čte data časy jako den, měsíc a rok, a ve Spojených státech je měsíc/den/rok.  
  
 V důsledku toho řetězec jako 20/01/2008 analyzovat do 20. ledna 2008 v Francie a poté vyvolat InvalidFormatException v USA.  
  
 Pokud chcete určit nastavení aktuální jazykové verze, můžete použít System.Globalization.CultureInfo.CurrentCulture.  
  
 Podívejte se na příklad níže pro jednoduchý příklad převod řetězce na typ dateTime.  
  
 Další příklady datum řetězců najdete v tématu <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>.  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)
