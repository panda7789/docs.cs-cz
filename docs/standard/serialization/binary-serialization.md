---
title: Binární serializace
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 34ba6cb658a52b647c6fbf9a4161d046f31cd73e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705818"
---
# <a name="binary-serialization"></a>Binární serializace

Serializace může být definován jako proces ukládání stavu objektu do úložiště média. Během tohoto procesu se veřejné a soukromé pole objektu a název třídy, včetně sestavení obsahující dané třídy, jsou převedeny do datového proudu bajtů, které jsou následně zapsána do datového proudu. Při objektu je následně deserializovat, je vytvořena přesné klon původní objekt.

Při provádění mechanismus serializace v prostředí objektově orientované, je třeba vytvořit počet kompromisy mezi snadnost použití a flexibilitu. Proces můžete automatizované do značné míry, za předpokladu, že budete mít dostatečné kontrolu nad procesem. Například může nastat situace, kde jednoduché binární serializace není dostatečné, nebo mohou existovat konkrétní důvod, proč se rozhodnout, která pole v třídě muset být serializován. Následující části prozkoumají robustní mechanizmus serializace, který je součástí .NET, a zvýrazní celou řadu důležitých funkcí, které vám umožní přizpůsobit proces tak, aby vyhovoval vašim potřebám.

> [!NOTE]
> Stav UTF-8 nebo UTF-7 objekt není zachováváno, je-li objekt je serializaci a deserializaci pomocí různých verzí rozhraní .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Vzhledem k tomu, že povaha binární serializace umožňuje úpravu privátních členů uvnitř objektu, a proto mění stav, budou doporučeny další serializace rozhraní, jako je JSON.NET, které fungují na veřejné ploše rozhraní API.

## <a name="binary-serialization-in-net-core"></a>Binární serializace v .NET Core

.NET Core podporuje binární serializaci s podmnožinou typů. Seznam podporovaných typů můžete zobrazit v [části serializovatelný typy](#serializable-types). Pro definovanou sadu typů jsou zaručena serializace mezi .NET Framework 4.5.1 a novějšími verzemi a .NET Core 2,0 a novějšími verzemi. Další implementace .NET, jako je mono, nejsou oficiálně podporované, ale měly by také fungovat.

### <a name="serializable-types"></a>Serializovatelné typy

- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.AccessViolationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.AggregateException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ApplicationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ArgumentException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ArgumentNullException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ArithmeticException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Array?displayProperty=nameWithType>
- <xref:System.ArraySegment%601?displayProperty=nameWithType>
- <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.BadImageFormatException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Boolean?displayProperty=nameWithType>
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>
- <xref:System.Collections.BitArray?displayProperty=nameWithType>
- <xref:System.Collections.Comparer?displayProperty=nameWithType>
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>
- <xref:System.Collections.Queue?displayProperty=nameWithType>
- <xref:System.Collections.SortedList?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Stack?displayProperty=nameWithType>
- `System.Collections.Generic.NonRandomizedStringEqualityComparer` (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích, serializace z .NET Framework do .NET Core není podporována.)
- <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ContextMarshalException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DBNull?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.2 a novějších verzích)
- <xref:System.Data.Common.DbException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.ConstraintException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.DataException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.DataSet?displayProperty=nameWithType>
- <xref:System.Data.DataTable?displayProperty=nameWithType> (Pokud nenastavíte RemotingFormat na SerializationFormat. Binary, v takovém případě se dá vyměnit jenom pomocí .NET Core 2,1 a novějších verzí.)
- <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.EvaluateException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>
- <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích, serializace z .NET Framework do .NET Core není podporována.)
- <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>
- <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.StrongTypingException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DataMisalignedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.DateTimeOffset?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- `System.Diagnostics.Contracts.ContractException` (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DivideByZeroException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.DllNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Drawing.Color?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- <xref:System.Drawing.PointF?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>
- <xref:System.Drawing.Size?displayProperty=nameWithType>
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>
- <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.EventArgs?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.6 a novějších verzích)
- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.ExecutionEngineException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.FieldAccessException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.FormatException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>
- <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- `System.IO.Compression.ZLibException` (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.FileFormatException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.FileLoadException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.IOException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.InvalidDataException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.InsufficientMemoryException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IntPtr?displayProperty=nameWithType>
- <xref:System.InvalidCastException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.InvalidOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.InvalidProgramException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.MemberAccessException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.MethodAccessException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.MissingFieldException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.MissingMemberException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.MissingMethodException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.Cookie?displayProperty=nameWithType>
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>
- <xref:System.Net.CookieException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.HttpListenerException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.WebException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.NotFiniteNumberException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.NotImplementedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.NotSupportedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.NullReferenceException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.ObjectDisposedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.OperationCanceledException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.OutOfMemoryException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.OverflowException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.RankException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích, serializace z .NET Framework do .NET Core není podporována.)
- <xref:System.Reflection.TargetException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.HostProtectionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.SecurityException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích, omezená data serializace)
- <xref:System.Security.VerificationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.StackOverflowException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.SystemException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>
- <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.TimeoutException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Transactions.TransactionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Tuple?displayProperty=nameWithType>
- <xref:System.TypeAccessException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.TypeInitializationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.TypeLoadException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.TypeUnloadedException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.UIntPtr?displayProperty=nameWithType>
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.UriFormatException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.ValueTuple?displayProperty=nameWithType> (neserializovatelné v .NET Framework 4,7 a dřívějších verzích)
- <xref:System.ValueType?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:System.WeakReference%601?displayProperty=nameWithType>
- <xref:System.WeakReference?displayProperty=nameWithType>
- <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Xml.XmlException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)
- <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> (k dispozici v .NET Core 2.0.4 a novějších verzích)

## <a name="in-this-section"></a>V tomto oddílu

- [Koncepty serializace](../../../docs/standard/serialization/serialization-concepts.md)\
Popisuje dva scénáře, kde je serializace užitečná: Pokud zachovává data do úložiště a při předávání objektů mezi doménami aplikace.

- \ [Základní serializace](../../../docs/standard/serialization/basic-serialization.md)
Popisuje, jak používat binárního souboru a SOAP formátovacích modulů k serializaci objektů.

- \ [selektivní serializace](../../../docs/standard/serialization/selective-serialization.md)
Popisuje, jak zabránit serializována některé členy třídy.

- \ [vlastní serializace](../../../docs/standard/serialization/custom-serialization.md)
Popisuje, jak přizpůsobit serializaci pro třídu pomocí rozhraní <xref:System.Runtime.Serialization.ISerializable>.

- [Kroky v procesu serializace](../../../docs/standard/serialization/steps-in-the-serialization-process.md)\
Popisuje kurz akce serializace trvá, když <xref:System.Runtime.Serialization.Formatter.Serialize%2A> metoda je volána na formátovacím modulem.

- \ [serializace odolná proti verzím](../../../docs/standard/serialization/version-tolerant-serialization.md)
Vysvětluje, jak vytvořit Serializovatelné typy, které lze upravit v čase bez způsobení aplikací k vyvolání výjimky.

- [Pokyny serializace](../../../docs/standard/serialization/serialization-guidelines.md)\
Poskytuje některé obecné pokyny pro rozhodování, kdy k serializaci objektu.

## <a name="reference"></a>Odkaz

- <xref:System.Runtime.Serialization>\
Obsahuje třídy, které lze použít pro serializaci a deserializaci objektů.

## <a name="related-sections"></a>Související oddíly

- \ [serializace XML a SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
Popisuje mechanismus serializace XML, který je součástí common language runtime.

- \ [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)
Popisuje zabezpečené kódování zásady dodržovat při psaní kódu, který provede serializaci.

- \ [vzdálené komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))
Popisuje různé komunikační metody k dispozici v rozhraní .NET Framework pro vzdálenou komunikaci.

- [Webové služby XML vytvořené pomocí ASP.NET a klientů webové služby xml](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
Poskytuje témata, které popisují a vysvětluje, jak programovat webové služby XML pomocí ASP.NET.
