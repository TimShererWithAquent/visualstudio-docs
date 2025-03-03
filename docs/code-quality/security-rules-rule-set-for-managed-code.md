---
title: Security Rules rule set for managed code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "dotnet"
---
# Security Rules rule set for managed code

Use the Microsoft Security Rules rule set for legacy code analysis to maximize the number of potential security issues that are reported.

|Rule|Description|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Review SQL queries for security vulnerabilities|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Catch non-CLSCompliant exceptions in general handlers|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Review imperative security|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Do not declare read only mutable reference types|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Array fields should not be read only|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Secure asserts|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Review deny and permit only usage|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Review declarative security on value types|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Review visible event handlers|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Pointers should not be visible|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Secured types should not expose fields|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Method security should be a superset of type|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Call GC.KeepAlive when using native resources|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA methods should only call APTCA methods|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA types should only extend APTCA base types|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Review SuppressUnmanagedCodeSecurityAttribute usage|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Seal methods that satisfy private interfaces|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Secure serialization constructors|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Static constructors should be private|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Do not indirectly expose methods with link demands|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Override link demands should be identical to base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Wrap vulnerable finally clauses in outer try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Type link demands require inheritance demands|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Security critical constants should be transparent|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Security critical types may not participate in type equivalence|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Default constructors must be at least as critical as base type default constructors|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegates must bind to methods with consistent transparency|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Methods must keep consistent transparency when overriding base methods|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Level 2 assemblies should not contain LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Members should not have conflicting transparency annotations|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparent methods must contain only verifiable IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparent methods must not call methods with the SuppressUnmanagedCodeSecurity attribute|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Transparent methods may not use the HandleProcessCorruptingExceptions attribute|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparent code must not reference security critical items|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparent methods must not satisfy LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Transparent code should not be protected with LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Transparent methods should not use security demands|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Transparent code should not load assemblies from byte arrays|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Transparent methods should not be decorated with the SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Types must be at least as critical as their base types and interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparent methods may not use security asserts|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparent methods must not call into native code|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Assemblies should have valid strong names|
|[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)|Do not use insecure deserializer BinaryFormatter|
|[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)|Do not call BinaryFormatter.Deserialize without first setting BinaryFormatter.Binder|
|[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)|Ensure BinaryFormatter.Binder is set before calling BinaryFormatter.Deserialize|
|[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md)|Do not use insecure deserializer LosFormatter|
|[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)|Do not use insecure deserializer NetDataContractSerializer|
|[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)|Do not deserialize without first setting NetDataContractSerializer.Binder|
|[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)|Ensure NetDataContractSerializer.Binder is set before deserializing|
|[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md)|Do not use insecure deserializer ObjectStateFormatter|
|[CA2321](ca2321.md)|Do not deserialize with JavaScriptSerializer using a SimpleTypeResolver|
|[CA2322](ca2322.md)|Ensure JavaScriptSerializer is not initialized with SimpleTypeResolver before deserializing|
|[CA3001](../code-quality/ca3001-review-code-for-sql-injection-vulnerabilities.md)|Review code for SQL injection vulnerabilities|
|[CA3002](../code-quality/ca3002-review-code-for-xss-vulnerabilities.md)|Review code for XSS vulnerabilities|
|[CA3003](../code-quality/ca3003-review-code-for-file-path-injection-vulnerabilities.md)|Review code for file path injection vulnerabilities|
|[CA3004](../code-quality/ca3004-review-code-for-information-disclosure-vulnerabilities.md)|Review code for information disclosure vulnerabilities|
|[CA3005](../code-quality/ca3005-review-code-for-ldap-injection-vulnerabilities.md)|Review code for LDAP injection vulnerabilities|
|[CA3006](../code-quality/ca3006-review-code-for-process-command-injection-vulnerabilities.md)|Review code for process command injection vulnerabilities|
|[CA3007](../code-quality/ca3007-review-code-for-open-redirect-vulnerabilities.md)|Review code for open redirect vulnerabilities|
|[CA3008](../code-quality/ca3008-review-code-for-xpath-injection-vulnerabilities.md)|Review code for XPath injection vulnerabilities|
|[CA3009](../code-quality/ca3009-review-code-for-xml-injection-vulnerabilities.md)|Review code for XML injection vulnerabilities|
|[CA3010](../code-quality/ca3010-review-code-for-xaml-injection-vulnerabilities.md)|Review code for XAML injection vulnerabilities|
|[CA3011](../code-quality/ca3011-review-code-for-dll-injection-vulnerabilities.md)|Review code for DLL injection vulnerabilities|
|[CA3012](../code-quality/ca3012-review-code-for-regex-injection-vulnerabilities.md)|Review code for regex injection vulnerabilities|
